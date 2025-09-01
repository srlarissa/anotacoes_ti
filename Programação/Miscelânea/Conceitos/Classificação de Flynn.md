A **Classificação de Flynn** é um esquema fundamental para categorizar as arquiteturas de computadores paralelos, proposta com base na **quantidade de instruções e dados que são processados simultaneamente** em um determinado momento. Essa classificação ajuda a entender como os sistemas de computação lidam com o paralelismo em nível de hardware.

### As classificações se dividem nas quatro categorias abaixo:

1. **SISD (Single Instruction, Single Data):**

Este é o modelo de computador **sequencial mais comum e básico**. Em um sistema SISD, existe **um único contador de programa**, o que significa que **apenas uma instrução é executada de cada vez** e essa instrução opera sobre **um único fluxo de dados**. As instruções são processadas estritamente em sequência, uma após a outra. 

Computadores históricos como o Univac 1, IBM 360, CDC 7600, e até mesmo um laptop moderno (quando executando uma única sequência de instruções) são exemplos de sistemas SISD.

A [programação sequencial](C:\Users\laris\Documents\Estudo\Obsidian\anotacoes_ti\Programação\Miscelânea\Conceitos\Programação Sequencial.md) se alinha perfeitamente com a arquitetura SISD, onde o programa é uma série de instruções executadas linearmente por uma única UCP. No entanto, existem limites físicos e termodinâmicos para o aumento contínuo da velocidade em sistemas sequenciais, o que impulsionou o desenvolvimento da computação paralela.

2. **SIMD (Single Instruction, Multiple Data):**

Em uma arquitetura SIMD, existe **um único contador de programa** e **uma única instrução é executada por diversos processadores simultaneamente**, porém, cada processador opera sobre **diferentes dados**. Isso significa que todas as Unidades Centrais de Processamento (UCPs) executam a mesma instrução de forma **síncrona**, mas com conjuntos de dados distintos. É considerado o **nível mais interno de paralelismo**.

Processadores vetoriais e arrays de processadores utilizam essa arquitetura. As **GPUs (Graphical Processing Units)** são um exemplo proeminente de processadores que utilizam a arquitetura SIMD. Historicamente, essa abordagem foi implementada com o CRAY-1 e ressurgiu em processadores comuns em 1997 com instruções como MMX, SEE, AVX e AVX-512.

3. **MISD (Multiple Instruction, Single Data):**

Neste modelo, **um único fluxo de dados é executado por várias UCPs**, cada uma utilizando **instruções diferentes**. A ideia é que múltiplos processadores executem operações distintas sobre a mesma informação.

Existem **poucos exemplos reais** de arquiteturas deste tipo. Embora seja uma categoria teórica importante para completar a classificação de Flynn e para a competição entre algoritmos, sua aplicação prática é limitada.

4. **MIMD (Multiple Instruction, Multiple Data)**

O MIMD é o **tipo mais comum de computador paralelo**. Nesta arquitetura, existem **vários contadores de programa**, permitindo que **cada UCP execute instruções diferentes** e opere sobre **dados diferentes**. Isso oferece a maior flexibilidade para o paralelismo.

**Supercomputadores, clusters, grades computacionais (Grids) e processadores multi-core** são todos exemplos de sistemas MIMD

Os sistemas MIMD podem ser ainda mais detalhados com base em dois critérios: o **espaço de endereçamento** e o **mecanismo de comunicação**. Eles podem ser agrupados em quatro grupos principais:

- **SMPs (Symmetric MultiProcessors)** 
	- **Espaço de Endereçamento**: Caracterizam-se por um **único espaço de endereçamento lógico** e uma **memória centralizada**, onde todos os processadores acessam o mesmo espaço de memória global. As mudanças feitas na memória por um processador são visíveis a todos os outros;
	- **Mecanismo de Comunicação**: A comunicação entre os processadores é realizada através de **operações de leitura (loads) e escrita (stores)** diretamente na memória compartilhada;
	- **Características**: São sistemas **homogêneos**, com **compartilhamento total da mesma memória** e uma única cópia do Sistema Operacional. Apresentam uma imagem única do sistema e excelente conectividade, sendo **fortemente acoplados**;
	- **Limitações**: Aumentar o número de processadores em SMPs leva a um aumento do tráfego na interconexão entre processadores e memória, causando instabilidade e **limitando a escalabilidade**. O programador é responsável pela sincronização do acesso à memória compartilhada para evitar erros;
	- **Exemplos**: Multi-core processors são uma instância especial de máquinas paralelas com memória compartilhada. Outros exemplos incluem Sun HPC 10000 (StarFire), SGI Altix, SGI Origin, IBM pSeries e Compac AlphaServer.
	

- **MPPs (Massively Parallel Processors)**: 
	- **Espaço de Endereçamento**: Diferem na implementação física e possuem **múltiplos processadores com memória privativa**. O espaço de endereçamento **não é compartilhado**, configurando uma arquitetura de **memória distribuída**. Cada processador acessa apenas sua memória local, e mudanças em uma memória local não afetam outras;
	- **Mecanismo de Comunicação**: A comunicação entre processadores é feita por **troca explícita de mensagens** através de uma **rede de interconexão**. Essa rede pode ter diferentes topologias. O programador é responsável pelo compartilhamento de dados e pelo envio e recebimento de mensagens;
	- **Características**: São sistemas **escaláveis** e **fracamente acoplados**. Podem ser homogêneos ou heterogêneos, e cada nó executa sua própria cópia do Sistema Operacional. Embora haja uma imagem única do sistema em relação aos sistemas de arquivos, um escalonador de tarefas pode criar partições dedicadas para diferentes aplicações. Aplicações não compartilham recursos, podendo entrar em estado de espera;
	- **Vantagens**: A quantidade de memória aumenta proporcionalmente ao número de processadores, e cada processador acessa sua memória de forma independente. Podem ser construídos a partir de processadores e redes existentes;
	- **Exemplos**: Cray T3E, IBM SP2s e clusters montados pelos próprios usuários com o propósito de serem MPPs.
	
- **Clusters ou NOWs (Network Of Workstations)**: 
	- **Espaço de Endereçamento e Comunicação**: Semelhante aos MPPs, os nós de um cluster (estações de trabalho ou PCs) possuem memória privativa e se comunicam através de **redes locais**;
	- **Diferenças dos MPPs**: A principal distinção é a **ausência de um escalonador centralizado** e o uso de **redes de interconexão mais lentas**;
	- **Características**: Cada nó possui seu próprio escalonador local, e os recursos são **compartilhados** sem partições dedicadas a uma aplicação. As aplicações devem considerar o impacto no desempenho, pois o sistema não é dedicado;
	- **Vantagens**: A principal vantagem é a possibilidade de compor um sistema de alto desempenho com **baixo custo**, especialmente em comparação com os MPPs;
	- **Conceito**: A Computação em Cluster foi estendida para computação através de sites distribuídos geograficamente, conectados por redes metropolitanas, evoluindo para a Computação em Grid.
	
- **Grades Computacionais (Computational Grids)**: 
	- **Espaço de Endereçamento e Comunicação**: Utilizam computadores **independentes e geograficamente distantes**, interligados por redes como a Internet. A comunicação é tipicamente por troca de mensagens, mas a heterogeneidade e a distância impõem desafios adicionais;
	- **Diferenças dos Clusters**: As grades se distinguem pela **heterogeneidade de recursos**, **alta dispersão geográfica** (escala mundial), múltiplos domínios administrativos e **controle totalmente distribuído**;
	- **Componentes**: Podem ser compostas por uma variedade de plataformas, incluindo PCs, SMPs, MPPs e clusters;
	- **Gerenciamento e Desafios**: São controladas por diferentes entidades e, a princípio, não possuem uma imagem única do sistema. Para gerenciar essa complexidade, propostas de **middlewares de gerenciamento** atuam como uma camada entre a infraestrutura e as aplicações. As aplicações devem ser preparadas para o **dinamismo**, a **variedade de plataformas** e, crucialmente, para **tolerar falhas**, que são mais frequentes em ambientes de grade devido à dispersão e independência dos recursos. O gerenciamento da execução da aplicação, através de políticas de escalonamento e balanceamento de carga, é fundamental para a utilização eficiente;
	- **Visão:** O conceito de Grid Computing busca oferecer desempenho computacional de forma eficiente, sob demanda e a custo razoável para qualquer um que precise, inspirando-se no modelo de rede elétrica;
	- **Exemplo Conceitual**: SETI@home é um exemplo clássico de uso de recursos globais para um problema computacional distribuído, onde computadores conectados à internet contribuíam com tempo ocioso para analisar dados de radiotelescópios.
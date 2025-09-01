### Definição:

A **Programação Paralela** é um paradigma de computação que surgiu da necessidade de superar os **limites físicos e termodinâmicos do processamento sequencial** e da crescente demanda computacional para problemas complexos. Ao invés de um programa ser executado por uma única Unidade Central de Processamento (UCP) que processa uma instrução de cada vez em sequência, a programação paralela envolve a **decomposição de um problema em várias partes** que podem ser executadas **concorrentemente**. Cada uma dessas partes, por sua vez, é constituída de uma sequência de instruções executadas simultaneamente por diferentes UCPs.

### Recursos:

Os recursos computacionais utilizados para a programação paralela podem ser configurados de diversas formas:

1. **Multiprocessamento**: Um único computador com múltiplos processadores.

2. **Multicomputação**: Um número de computadores conectados através de uma rede.

3. **Combinação de ambos**: A arquitetura mais comum atualmente. Isso inclui máquinas paralelas de memória distribuída (várias máquinas independentes interconectadas por uma rede) e de memória compartilhada (vários processadores independentes compartilhando a mesma memória global), sendo processadores multi-core uma instância especial de memória compartilhadas.

### Aplicações:

A programação paralela é ideal para problemas que:

1. Podem ser **decompostos em partes** que podem ser resolvidas de forma simultânea.

2. Requerem a execução de **muitas instruções ao mesmo tempo**.

3. Podem ser resolvidos em **menor tempo** utilizando múltiplas UCPs do que apenas uma. Muitos problemas reais têm uma natureza intrinsecamente paralela.

### Objetivos:

As principais motivações para usar a programação paralela incluem:

1. **Economizar tempo e/ou dinheiro**: Ao reduzir o tempo total de execução.

2. **Resolver problemas maiores**: Problemas que não seriam viáveis em um tempo razoável com recursos sequenciais.

3. **Prover concorrência real**: Utilizando recursos globais, como exemplificado pelo projeto SETI@home.

4. **Aumentar desempenho e capacidade de memória**: Distribuindo o trabalho e os dados entre múltiplos processadores.

5. **Lidar com recursos independentes** e fazer com que usuários e computadores trabalhem em colaboração.

### Níveis de concorrência:

A concorrência na computação pode existir em diferentes níveis: hardware, Sistema Operacional e aplicação. A arquitetura de computadores paralelos é classificada pela [Classificação de Flynn](obsidian://open?vault=Obsidian&file=anotacoes_ti%2FPrograma%C3%A7%C3%A3o%2FMiscel%C3%A2nea%2FConceitos%2FClassifica%C3%A7%C3%A3o%20de%20Flynn), baseada na quantidade de fluxos de instruções e dados processados simultaneamente.

### Por que utilizar programação paralela:

A Programação Paralela é utilizada por uma série de motivos cruciais, impulsionados principalmente pela necessidade de superar as **limitações da computação sequencial** e pela crescente complexidade e demanda por poder computacional em diversas áreas, como as listadas abaixo:

1. **Superar os Limites Físicos e Termodinâmicos do Processamento Sequencial**: Há um **limite na velocidade de transmissão dos sinais elétricos**, imposto pela velocidade da luz, que exige a aproximação dos componentes. Também existem **limites de miniaturização** dos chips e **restrições termodinâmicas** que causam superaquecimento, impedindo o aumento contínuo da velocidade de um único processador. Em vez de buscar o máximo de desempenho em um único processador, tornou-se mais **econômico e eficiente utilizar vários processadores mais baratos** trabalhando em conjunto

2. . **Atender à Demanda Computacional Crescente e Resolver Problemas Complexos**: A demanda por computação tem aumentado exponencialmente em áreas como visualização, bancos de dados distribuídos e simulações complexas. A programação paralela permite **resolver problemas maiores** que não seriam viáveis em um tempo razoável com abordagens sequenciais.

3. **Otimizar Tempo e Reduzir Custos Financeiros**: Ao distribuir o trabalho entre vários processadores, a programação paralela visa **reduzir o tempo total de execução** de uma aplicação. Essa economia de tempo pode se traduzir em **economia de dinheiro**, tornando o processo computacional mais eficiente financeiramente.

4. **Aumentar o Desempenho e a Capacidade de Memória**: O objetivo principal é **aumentar o desempenho** dos programas, garantindo que o tempo de execução seja o menor possível, que é a principal meta da Computação de Alto Desempenho (HPC. Permite **aumentar a capacidade de memória** ao utilizar a memória de múltiplos processadores, distribuindo os dados.

5. **Prover Concorrência Real e Colaboração**: A programação paralela permite a **concorrência real** onde múltiplos processos ou threads competem ou colaboram por recursos. É utilizada para **lidar com recursos independentes** e fazer com que usuários e computadores trabalhem em colaboração.

6. **Ampla Aplicabilidade em Diversos Domínios**: Inicialmente, foi utilizada para resolver **problemas difíceis nas áreas de ciência e engenharia**, como meteorologia, física, biociências (incluindo sequenciamento de genomas e dobramento de proteínas), geologia, microeletrônica, e ciência da computação. Exemplos de grandes desafios incluem química quântica, astrofísica, dinâmica de fluidos e projeto de novos materiais

### Hardware

As arquiteturas que utilizam paralelismo em hardware se baseiam em:

1. Múltiplas unidades de execução;
2. Instruções pipelined;
3. Múltiplos núcleos (multi-core).




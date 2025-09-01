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

A concorrência na computação pode existir em diferentes níveis: hardware, Sistema Operacional e aplicação. A arquitetura de computadores paralelos é classificada pela [Classificação de Flynn](obsidian://open?vault=Obsidian&file=anotacoes_ti%2FPrograma%C3%A7%C3%A3o%2FMiscel%C3%A2nea%2FConceitos%2FClassifica%C3%A7%C3%A3o%20de%20Flynn), baseada na quantidade de fluxos de instruções e dados processados simultaneamente



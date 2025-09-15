# Análise preliminar

### Qual o trabalho?

 O estudo e análise minuciosa de um benchmark entre um supercomputador (Beskow - Cray XC40) e a nuvem da AWS.

### Quem é o autor?

**Tamara Dancheva:**

> Estudante de doutorado no Basque Center for Applied Mathematics, com mestrado em Engenharia Computacional pela Universidade de Strasbourg e bacharelado em Ciência da Computação e Engenharia. Sua pesquisa foca em mecânica computacional e HPC.

******

**Unai Alonso:**

> Especialista em modelagem termomecânica de processos de usinagem e participou de vários projetos nacionais e internacionais. Trabalhou no centro de pesquisa Ideko S.Coop e nas Universidades de Magdeburg e ENSAM na França.

****

**Dr. Michael Barton:**

> Pesquisador Associado Ikerbasque e Pesquisador Ramon & Cajal 2017 no BCAM. Antes de ingressar no BCAM, foi pós-doutorando na JKU Linz (Áustria), Technion (Israel) e King Abdullah University of Science and Technology (KAUST, Arábia Saudita). Publicou mais de 50 artigos de pesquisa revisados por pares, com foco em análise numérica, modelagem e processamento geométrico, e aproximação e racionalização de objetos curvos (NURBS).

### Quais contribuições foram feitas?

> Benchmarking e análise de desempenho da aplicação conduzidas tanto na **Amazon EC2** quanto no **supercomputador Beskow (Cray XC40)**, seguidas por uma **análise comparativa detalhada**. Ao longo do processo, o estudo explica e **destaca tendências gerais que são relevantes para este tipo de estudos de viabilidade**.

> O trabalho **demonstra como e por que o desempenho de uma aplicação HPC de dinâmica de fluidos computacional (CFD) em larga escala na AWS compete muito de perto com o supercomputador Beskow** em termos de custo-eficiência, com escalabilidade forte.

> Além disso, o estudo fornece evidências de uma mudança que começou em 2020, indicando que a nuvem está se aproximando dos supercomputadores on-premise em termos de desempenho para aplicações HPC, principalmente devido aos avanços recentes nas tecnologias de rede como o Elastic Fabric Adapter (EFA).
### Qual a estratégia utilizada na abordagem?

Foi utilizada uma abordagem de benchmarking extenso em ambos ambientes:

**Micro benchmarks OSU:**

> Foram realizados **micro benchmarks OSU (Ohio State University)** para quantificar os blocos construtivos básicos de um programa separadamente, focando na latência e largura de banda da comunicação ponto a ponto e rotinas MPI coletivas.

**Macro benchmarks NASA:**

> Foram executados **macro benchmarks NASA** (NAS Parallel Benchmarks), que são representativos de uma vasta gama de categorias de aplicações científicas, particularmente aquelas de alto throughput ou fortemente acopladas.

O estudo focou na análise de desempenho de uma **aplicação de dinâmica de fluidos computacional (CFD)** de grande escala, implementada na plataforma FEniCS-HPC. Esta análise incluiu a avaliação de **escalabilidade forte (strong scaling)**, que mede como o tempo de execução diminui à medida que o número de processos aumenta para um tamanho de problema fixo.     ◦ Foi realizado **profiling** da aplicação utilizando o Integrated Performance Monitor (IPM) para identificar as rotinas MPI que consomem mais tempo e coletar estatísticas sobre o tamanho das mensagens.

Ao longo do processo, o estudo procurou **explicar e destacar tendências gerais** que são relevantes para este tipo de estudos de viabilidade, além de **identificar os fatores subjacentes que levam a um desempenho aprimorado**. Esses fatores incluem aspectos como desempenho de rede (com destaque para o Elastic Fabric Adapter - EFA na AWS), poder computacional, velocidade de armazenamento, detalhes de implementação MPI e ajuste de algoritmos. Assim, a estratégia principal foi a de realizar uma **investigação incremental**, começando com micro benchmarks, avançando para macro benchmarks e, finalmente, avaliando uma aplicação real de HPC, comparando exaustivamente o desempenho em um ambiente de nuvem e um supercomputador on-premise.
### Qual lacuna ou problema está tentando resolver?

O estudo busca responder o seguinte questionamento: 

> **O desempenho de aplicações de HPC (High-Performance Computing) na nuvem pode se igualar ao das infraestruturas on-premise (locais)**?

Dessa forma, a lacuna específica que este trabalho preenche é a **escassez de evidências recentes na academia que demonstrem o desempenho de aplicações HPC em nuvem** desde as mudanças tecnológicas introduzidas, especialmente para **aplicações HPC fortemente acopladas**. O maior gargalo identificado para a execução de aplicações HPC na nuvem tem sido a **rede**, por um grande consenso.
### Em quais trabalhos anteriores ou teorias essa pesquisa se fundamenta?

**Linha do tempo:** 

> Ainda em 2008, estudos iniciais apontaram que a nuvem ainda não estava madura o bastante para ser utilizada em operações HPC. 

> Em 2011, apesar de pequenas melhoras, a rede disponível não era equivalente à interconexão de alto desempenho dos supercomputadores.

> Já em 2017, o AWS Nitro System trouxe a divisão de tarefas, deixando cada parte dedicada para apenas uma função, o que fez com que o hipervisor ganhasse mais desempenho, o custo caísse e a segurança aumentasse *(uma vez que agora não temos mais acesso administrativo humano)*. 

> Mais recentemente, em 2019, o Elastic Fabric Adapter (EFA), foi anunciado para comunicação de baixa latência *(comunicação direta e de alta velocidade entre nós, ao invés de ter que passar pela burocracia do S.O primeiro)*.
### Qual a aplicabilidade prática ou teorica dessa pesquisa?

Como resultado dessa pesquisa, temos algumas aplicações práticas como produto, tais quais:

**Guia de migração de Pesquisas para a Nuvem:**

> O estudo demonstra como pesquisadores podem **escalar e avaliar o desempenho de suas aplicações na nuvem**. Os resultados detalhados dos benchmarks de micro e macro servem como **indicadores para que outros pesquisadores façam previsões sobre o desempenho de suas aplicações HPC** caso decidam migrar suas pesquisas para a nuvem. Isso oferece um guia prático para a tomada de decisões.

**Modelo para Estudos Comparativos:**

> O procedimento geral delineado no estudo para avaliar o desempenho de aplicações e as tendências descritas podem servir como um **modelo para qualquer estudo comparativo desse tipo**, independentemente da plataforma em nuvem ou da infraestrutura on-premise.

**Soluções de HPC Custo-Eficientes:**

> A pesquisa mostra que o desempenho de aplicações HPC na AWS **compete muito de perto com o supercomputador Beskow em termos de custo-eficiência**. Destaca que empresas pequenas e indivíduos podem ter acesso à infraestrutura de TI necessária sem grandes investimentos em hardware e manutenção. A utilização de **instâncias spot** é apresentada como uma **solução custo-eficaz** para necessidades não críticas, com economias significativas em relação às instâncias sob demanda.

**Validação da Escalabilidade na Nuvem:**

> O trabalho **demonstra a escalabilidade forte (strong scaling) satisfatória** de uma aplicação CFD de larga escala na nuvem AWS EC2 para **até 2304 processos**, com desempenho altamente competitivo em relação ao Beskow. Isso valida a capacidade da nuvem para lidar com cargas de trabalho HPC massivamente paralelas.

**Utilização de Novas Tecnologias em Nuvem:**

> O estudo destaca o papel de avanços como o **Elastic Fabric Adapter (EFA)** da AWS, que "aceleraram ainda mais a convergência de HPC e computação em nuvem". A pesquisa mostra como tecnologias como o EFA e o Nitro Hypervisor contribuem para **reduzir a sobrecarga de virtualização e melhorar o desempenho da rede**, oferecendo insights práticos sobre como alavancar essas funcionalidades.


### Pergunta:

Ambas máquinas, a Beskow e a máquina na AWS utilizam arquitetura Intel. Acredita que haveria mudanças significativas caso a arquitetura fosse outra?
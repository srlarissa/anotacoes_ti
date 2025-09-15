### Qual o trabalho?

O cerne do trabalho em questão é **apresentar uma metodologia para migrar um sistema de recomendação baseado em modelos de deep learning para plataformas de Machine Learning (ML) e arquiteturas serverless na nuvem**. Além disso, o trabalho realiza uma **avaliação experimental dessas plataformas** e discute o **equilíbrio entre desempenho e custo** ao utilizar a infraestrutura de nuvem.

### Quem é o autor?

Os autores do estudo são **Dheeraj Chahal, Mayank Mishra, Surya Palepu e Rekha Singhal**. Todos eles são pesquisadores do TCS Research, localizado em Mumbai, Índia.

### Quais contribuições foram feitas?

**Apresentar um esquema para migrar um sistema de recomendação baseado em ML para a nuvem:**

 > O trabalho detalha a metodologia de migração do sistema de recomendação NISER *(um modelo baseado em redes neurais de grafos - GNN)* para plataformas de nuvem, especificamente utilizando AWS SageMaker e AWS Lambda.
 
 **Estudar o desempenho da inferência e o custo incorrido utilizando diferentes tipos de instâncias disponíveis na nuvem:**

> Isso envolveu a avaliação de instâncias de CPU *(ml.c5.xlarge, ml.c5.2xlarge)* e GPU *(ml.g4dn.xlarge, ml.g4dn.2xlarge)* do AWS SageMaker, bem como a configuração de instâncias do AWS Lambda. O estudo analisou o desempenho em termos de tempo de resposta com o aumento da concorrência e o custo por inferência.

**Comparar o desempenho e o custo quando um sistema de recomendação é implantado usando uma plataforma de ML (AWS SageMaker) versus uma plataforma serverless (AWS Lambda):**

> Esta é destacada como a **primeira tentativa conhecida de comparar uma plataforma de ML e uma arquitetura serverless para a implantação de um sistema de recomendação baseado em modelos de deep learning**. A comparação explorou como o tempo de resposta e o custo variam entre essas duas abordagens, considerando cenários de baixa e alta concorrência.

Em suma, o estudo visa ajudar as organizações a tomar decisões informadas sobre a escolha do serviço e da infraestrutura de nuvem mais adequados para cargas de trabalho de inteligência artificial, buscando o desempenho desejado com custo mínimo. O trabalho também discute o **equilíbrio entre desempenho e custo**, mostrando que o aumento de recursos a um custo mais alto nem sempre se traduz em um ganho proporcional no desempenho. As conclusões indicam que a arquitetura serverless pode oferecer melhor desempenho para cargas de trabalho "bursty" (com picos) devido à sua escalabilidade rápida e alta, enquanto as plataformas de ML são mais adequadas para cargas de trabalho de longa duração com uso otimizado de recursos.

### Qual a estratégia utilizada na abordagem?

A estratégia pode ser detalhada nos seguintes pontos:

1. **Metodologia de Migração:** O estudo apresenta uma metodologia para migrar um sistema de recomendação baseado em modelos de deep learning para a nuvem. Especificamente, o sistema de recomendação **NISER** (um modelo baseado em redes neurais de grafos - GNN - para recomendações baseadas em sessão) é utilizado como caso de estudo.

2. **Escolha das Plataformas de Nuvem:** São selecionadas duas plataformas da Amazon Web Services (AWS) para a implantação e avaliação:

    ◦ **AWS SageMaker:** Uma plataforma de ML bem conhecida para treinamento, implantação e inferência de modelos.

    ◦ **AWS Lambda:** Um serviço de plataforma serverless, conhecido por sua alta escalabilidade e modelo de pagamento por uso.

3. **Avaliação Experimental Abrangente:** O trabalho realiza uma avaliação experimental rigorosa do desempenho e do custo em diversas configurações:

    ◦ **Desempenho da Inferência:** É estudado o desempenho da inferência, medindo o tempo de resposta do sistema de recomendação sob diferentes níveis de concorrência (número de usuários concorrentes).

    ◦ **Custo Incorrido:** O custo por inferência é analisado, comparando os modelos de precificação do SageMaker e do Lambda.

    ◦ **Diferentes Tipos de Instâncias:** A avaliação inclui o uso de diferentes tipos de instâncias de CPU (e.g., ml.c5.xlarge, ml.c5.2xlarge) e GPU (e.g., ml.g4dn.xlarge, ml.g4dn.2xlarge) no AWS SageMaker para entender seu impacto no desempenho e custo.

    ◦ **Comparação entre Plataformas:** Um ponto central da estratégia é a **comparação direta do desempenho e custo entre a plataforma de ML (SageMaker) e a plataforma serverless (Lambda)**, que é um esforço pioneiro para sistemas de recomendação baseados em deep learning.

    ◦ **Análise On-Premise:** São realizados experimentos em servidores locais para estabelecer uma linha de base de desempenho para comparação com os resultados na nuvem.

4. **Análise de Trade-off:** O estudo discute explicitamente o **equilíbrio entre desempenho e custo** ao usar a infraestrutura de nuvem, observando que um aumento nos recursos a um custo mais alto nem sempre se traduz em um ganho proporcional no desempenho.

5. **Identificação de Cenários de Uso Otimizados:** A estratégia visa identificar em quais cenários cada tipo de plataforma (ML ou serverless) é mais vantajosa. Por exemplo, a arquitetura serverless pode ser melhor para cargas de trabalho com picos ("bursty workloads") devido à sua escalabilidade rápida, enquanto plataformas de ML podem ser mais adequadas para cargas de trabalho de longa duração com uso otimizado de recursos.

Em resumo, a estratégia central é a **avaliação comparativa empírica** das duas abordagens de implantação em nuvem para um sistema de recomendação de deep learning, com o objetivo de fornecer diretrizes práticas para a seleção de serviços de nuvem ideais em termos de desempenho e custo.

### Qual lacuna ou problema está tentando resolver?

Este estudo está visando preencher a lacuna de **falta de comparação experimental entre plataformas de Machine Learning (ML) e arquiteturas serverless para a implantação de sistemas de recomendação baseados em modelos de deep learning na nuvem**

### Em quais trabalhos anteriores ou teorias essa pesquisa se fundamenta?

**Extensão de um Trabalho Anterior**:

> O estudo explicitamente **estende o trabalho de Zheng et al.**, que conduziu uma pesquisa sobre serviços de nuvem para inferência de aprendizado de máquina com foco em custo-benefício e sensibilidade a Acordos de Nível de Serviço (SLO). O presente trabalho aprofunda essa linha de pesquisa ao comparar o desempenho de seu sistema de recomendação em diferentes tipos de servidores de endpoint do SageMaker e também ao comparar o desempenho do SageMaker com a plataforma serverless Lambda.

**Teoria do Modelo de Recomendação Utilizado**

> O sistema de recomendação empregado no estudo é o **NISER**, um modelo recentemente desenvolvido pelos próprios autores ou colaboradores. Este modelo NISER, por sua vez, é baseado em **redes neurais de grafos (GNN)**. Portanto, as teorias e conceitos de Deep Learning, particularmente as GNNs, formam a base teórica para o modelo central do estudo.

### Qual a aplicabilidade prática ou teorica dessa pesquisa?

A aplicabilidade do objeto de estudo, que se concentra na **migração e avaliação experimental de um sistema de recomendação baseado em deep learning (NISER) para plataformas de Machine Learning (ML) e arquiteturas serverless na nuvem**, possui tanto dimensões práticas quanto teóricas significativas.

**Orientação para Migração de Workloads de IA para a Nuvem:** 

> O trabalho oferece uma **metodologia para migrar um sistema de recomendação baseado em modelos de deep learning para a nuvem**, especificamente para AWS SageMaker e AWS Lambda. Isso é de grande utilidade para organizações que buscam levar suas cargas de trabalho de inteligência artificial de ambientes on-premise para a nuvem, aproveitando infraestrutura escalável e de baixo custo.

**Tomada de Decisão Informada sobre Serviços de Nuvem:** 

> O estudo aborda o desafio de "encontrar o serviço e a infraestrutura mais apropriados para uma dada aplicação que resulte no desempenho desejado com custo mínimo". As empresas podem usar as descobertas para **fazer escolhas judiciosas** sobre serviços de nuvem, tipos de instâncias e configurações, baseando-se em características da aplicação, requisitos de desempenho e orçamento disponível.

**Otimização da Implantação de Sistemas de Recomendação:** 

> Como os sistemas de recomendação são cruciais para "melhorar a experiência do cliente exibindo os itens mais relevantes", este estudo fornece **orientações práticas sobre como implantar esses sistemas eficientemente** em plataformas de ML ou arquiteturas serverless.

**Entendimento de Trade-offs entre Desempenho e Custo:** 

> A análise aprofundada do **equilíbrio entre desempenho e custo** ajuda os usuários a entender que "um aumento nos recursos a um custo mais alto não se traduz em um ganho proporcional no desempenho da aplicação". Isso permite escolher a infraestrutura que satisfaça os Acordos de Nível de Serviço (SLAs) e as restrições orçamentárias.

**Recomendação de Plataformas para Diferentes Cargas de Trabalho:** 

> As conclusões práticas indicam que a **arquitetura serverless (AWS Lambda) é mais adequada para cargas de trabalho "bursty" (com picos)** devido à sua escalabilidade rápida e alta, enquanto as **plataformas de ML (AWS SageMaker) são melhores para cargas de trabalho de longa duração** com uso otimizado de recursos.

**Estratégias para Mitigar "Cold Start":** 

> O estudo sugere que o uso da **plataforma de ML em conjunto com a arquitetura serverless pode mitigar o problema de "cold start"** em serverless, balanceando a carga para que o tráfego com picos seja redirecionado para o serverless sem a necessidade de provisionar cargas de trabalho de curta duração na plataforma de ML

### Pergunta:

A complexidade de combinar SageMaker e Lambda não pode gerar mais pontos de falha do que benefícios?



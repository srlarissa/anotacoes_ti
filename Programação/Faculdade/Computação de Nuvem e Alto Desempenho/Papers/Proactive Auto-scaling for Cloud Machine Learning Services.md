### Qual o trabalho?

O cerne do trabalho em questão é o desenvolvimento e a avaliação de um **método proativo de autoescalonamento vertical de containers para serviços de Machine Learning (ML) nativos da nuvem**. O objetivo principal é otimizar a utilização de recursos e reduzir custos para provedores de nuvem que oferecem serviços de ML, ao mesmo tempo em que previne erros de falta de memória (OOM) e degradação da Qualidade de Serviço (QoS).

### Quem é o autor?

• **David Buchaca** do _Barcelona Supercomputing Center Universitat Politecnica de Catalunya;
• **Josep LLuis Berral** do Barcelona Supercomputing Center Universitat Politecnica de Catalunya_;
• **Chen Wang** da _IBM Research Yorktown Heights, NY_;
• **Alaa Youssef** da _IBM Research Yorktown Heights, NY_.

### Quais contribuições foram feitas?

**Desenvolvimento de um Modelo de Previsão de Fases**:

> O trabalho propõe o uso de uma **Rede Neural Perceptron de Múltiplas Camadas (MLP) com janelas de tempo** para prever as próximas sequências de fases em containers com diferentes tipos de workload. Foi demonstrado que o MLP, juntamente com LSTM, oferece os melhores resultados de previsão (F1-score de 0.92 para previsão de um passo e 0.79 para previsão de quatro passos), sendo o MLP mais simples e rápido.

**Proposição de uma Política Proativa de Autoescalonamento Vertical**:

> Com base na previsão de fases, o estudo propõe uma **política preditiva de autoescalonamento vertical** para redimensionar dinamicamente o container. Esta política leva em conta as previsões futuras de uso de recursos, dimensionando apenas quando são previstas mudanças significativas, e aplicando tolerâncias para evitar redimensionamentos desnecessários.

**Melhoria na Eficiência e Redução de Custos**:

> A política preditiva demonstrou **reduzir em até 38% a CPU alocada** em comparação com as políticas padrão de provisionamento de recursos pelos desenvolvedores. Especificamente, o superprovisionamento de CPU foi reduzido de aproximadamente 10 * 10^8 CPU * hora para 6 * 10^8 CPU * hora. A política preditiva resulta em um **provisionamento de recursos mais ajustado**, com menos folga entre o limite e o uso real.

**Aumento da Estabilidade e Confiabilidade (Prevenção de Erros de OOM)**:

> A política preditiva **reduz drasticamente o número de erros de falta de memória (OOM) de centenas (350-402 em políticas reativas) para apenas 20**. Isso representa uma **prevenção de 96% dos OOMs** em cenários potenciais. A capacidade de prever transições abruptas de fase é a principal vantagem da política proativa, evitando interrupções do serviço devido a erros de OOM.

**Manutenção do Número de Operações de Redimensionamento**:

> A política de autoescalonamento proativo mantém o número de operações de redimensionamento próximo ao das melhores políticas reativas (cerca de 3-4 mudanças por container), o que é significativamente menor do que outras estratégias reativas (33 mudanças).
### Qual a estratégia utilizada na abordagem?

As estratégias utilizadas nesta abordagem de estudo são multifacetadas e podem ser divididas em três pilares principais: **descoberta incremental de fases de workload**, **previsão proativa de fases** e **políticas de autoescalonamento vertical proativo**.

1. **Descoberta Incremental de Fases de Workload**:

    ◦ **Utilização do Framework AI4DL**: A metodologia estende e coloca em prática o mecanismo de profiling para descoberta e classificação de comportamento descrito no framework AI4DL. Este framework monitora os recursos principais do container (CPU e consumo de Memória, podendo incluir GPU e IO).

    ◦ **Codificação de Traços (Trace encoding)**: A telemetria dos containers é codificada usando uma **Conditional Restricted Boltzmann Machine (CRBM)**. O CRBM é capaz de codificar séries temporais multidimensionais (CPU e memória ao longo do tempo, incluindo histórico) em um vetor de características, onde entradas semelhantes produzem codificações semelhantes.

    ◦ **Identificação de Fases (Phase identification)**: Os vetores de codificação gerados pelo CRBM, que possuem uma propriedade de "similaridade", são agrupados usando **métodos de clustering baseados em proximidade, como o k-means**. Cada cluster representa uma "fase" com um perfil de uso de recursos semelhante. O número de clusters (k) pode ser determinado durante o treinamento através de métodos clássicos (como observando a Soma dos Quadrados Dentro dos Clusters - SSW) ou de forma incremental.

    ◦ **Profiling Estatístico**: Para cada fase descoberta, são mantidas estatísticas de perfil para fornecer informações às políticas de alocação de recursos.

    ◦ **Mecanismo Incremental**: O estudo avança a tecnologia existente para um **método de descoberta de fases incremental**. Isso significa que, quando novos containers com diferentes tipos de aplicação introduzem novos comportamentos, o CRBM não precisa ser retreinado. Em vez disso, o método de clustering é atualizado, criando um novo modelo de clustering ou dividindo clusters divergentes e adicionando novos centros ao modelo de identificação de fases. Este método demonstrou ser eficaz na adaptação de modelos treinados em cargas de trabalho DLaaS para cargas de trabalho VR.

2. **Previsão Proativa de Fases (Phase Prediction)**:

    ◦ **Modelo de Previsão**: O estudo propõe o uso de uma **Rede Neural Perceptron de Múltiplas Camadas (MLP) com janelas de tempo** para prever a próxima sequência de fases de uma execução em andamento. Embora LSTMs (Long Short-Term Memory) tenham desempenho similar, o MLP foi escolhido por ser mais simples e rápido.

    ◦ **Processo de Previsão**: Dada uma sequência de fases descoberta de um container em execução em uma janela de tempo passada (t - d...t), o MLP é usado para prever as fases futuras (t+1...t+n).

    ◦ **Classificação de Fases**: A tarefa de previsão de fases é tratada como um problema de classificação, onde o classificador recebe como entrada uma janela de tempo de valores de fases e prevê as IDs das fases nos próximos _n_ intervalos de tempo.

    ◦ **Treinamento**: O modelo de previsão é treinado em uma coleção de sequências de fases de containers completos.

3. **Política de Autoescalonamento Vertical Proativo (Container Auto-scaling Policies)**:

    ◦ **Uso da Previsão de Fases**: Diferente das políticas reativas que apenas respondem a mudanças passadas, a política proativa aloca recursos com base na previsão do uso futuro de recursos, ou seja, prevendo as próximas fases e usando seus perfis para redimensionar o container proativamente.

    ◦ **Decisão de Redimensionamento**: A política decide o quanto provisionar levando em conta a "próxima janela" de previsões, escolhendo o máximo dos perfis candidatos para essa janela futura. As estatísticas para cada fase prevista são usadas, com a decisão de redimensionar o container de acordo com o uso máximo de recursos observado para essas fases.

    ◦ **Controle de Redimensionamento**: Para reduzir o número de ações de redimensionamento desnecessárias, os containers são escalonados apenas se a previsão indicar mudanças significativas de comportamento.

    ◦ **Tolerâncias**: Uma política de autoescalonamento é aplicada que prevê fases na próxima janela de tempo (1 minuto) e determina a demanda máxima de recursos de CPU e Memória de todos os perfis de fases previstos.

        ▪ **Escalonamento para Cima**: Se as demandas de recursos previstas indicarem um aumento acima de uma tolerância definida (por exemplo, 10% da demanda atual), o container é escalonado para cima com os recursos previstos.

        ▪ **Escalonamento para Baixo**: Quando os recursos previstos indicam uma diminuição da demanda abaixo do limite atual, o container é escalonado para baixo com uma tolerância maior para evitar que pequenas flutuações de uso causem escalonamentos frequentes.
### Qual lacuna ou problema está tentando resolver?

- **Ineficiência na Utilização de Recursos e Superprovisionamento**;
- **Dificuldade em Lidar com o Comportamento Dinâmico e Irregular de Workloads de ML**;
- **Limitações das Abordagens Reativas de Autoescalonamento**;
- **Deficiências dos Modelos Preditivos Existentes para Workloads de ML**;
- **Necessidade de Adaptação Incremental a Novos Tipos de Workloads**.

### Qual a aplicabilidade prática ou teorica dessa pesquisa?

- **Redução de Custos e Superprovisionamento de Recursos**;
- **Prevenção de Erros de Falta de Memória (OOM) e Melhoria da Qualidade de Serviço (QoS)**;
- **Gerenciamento Eficaz de Workloads de ML Dinâmicos**;
- **Autoescalonamento Vertical Proativo em Ambientes Cloud-Native**;
- **Adaptação a Diferentes Tipos de Workloads de ML**.
### Pergunta:


# Definição

O **ProvInCiA (Provenance in Smart Cities Approach)** é um **framework desenvolvido para coletar e gerenciar dados de proveniência em ecossistemas de Cidades Inteligentes (CIs)**. Ele foi criado para enfrentar o desafio da complexidade na coleta de proveniência em ambientes urbanos, que são naturalmente distribuídos e heterogêneos, com múltiplos programas, usuários e ferramentas envolvidos.

O principal objetivo da ProvInCiA é **garantir a rastreabilidade completa dos dados** em CIs, desde a coleta até o uso final. Isso é considerado essencial para **auditoria, transparência, legitimidade e confiabilidade** das políticas públicas e serviços urbanos baseados em dados. Ele busca resolver a limitação de abordagens existentes que se concentram em dataflows isolados, não sendo capazes de fornecer um rastro completo dos dados que permeiam diversas etapas e usuários.

# Meta-dataflow

Um dos diferenciais da ProvInCiA é a utilização do conceito de **meta-dataflow**, que é uma abstração que **associa múltiplos dataflows independentes**. Nela, o último dataset gerado por um dataflow serve como entrada inicial para o dataflow subsequente, criando um caminho de derivação contínuo e global dos dados. Essa abordagem permite representar caminhos de derivação complexos e ramificações (splits e merges), mas não pode conter ciclos, sendo grafos acíclicos direcionados (DAGs).

# Captura de dados

A ProvInCiA adota **três estratégias** para lidar com a heterogeneidade das fontes de dados de proveniência em CIs:

- **Instrumentação de código**: Desenvolvedores inserem chamadas à API da ProvInCiA diretamente nos scripts ou aplicações. Essa abordagem é recomendada quando o código-fonte está disponível e permite explicitar as transformações dos dados;

- **Escuta ativa (Eavesdrop)**: Um componente monitora o ambiente de execução (e.g., terminal do sistema operacional) para identificar transformações de dados realizadas por meio de comandos do usuário;

- **Análise de arquivos de logs (Crawler)**: O framework acessa arquivos de log existentes, extrai dados de proveniência relevantes e os importa. O Crawler precisa ser customizado para cada tipo de log.

# Arquitetura e Componentes

São ao todo nove:

- **Eavesdrop, API de Acesso e Crawler**: Responsáveis pela captura dos dados brutos de proveniência;

- **Broker de Proveniência**: Atua como uma fila de processamento para as requisições de proveniência;

- **Estruturador de Proveniência**: Identifica e estrutura os elementos do modelo PROV (entidades, atividades e agentes) e identifica meta-dataflows. Em seguida, os registra no Banco de Dados de Proveniência;

- **Banco de Dados de Proveniência**: Armazena os dados de proveniência. Estende o esquema da ferramenta DfAnalyzer e inclui conceitos como meta-dataflow, além de classes para proveniência prospectiva (p-prov), retrospectiva (r-prov) e dados de domínio;

- **Processador de Consultas**: Permite a submissão de consultas (atualmente SQL) aos dados de proveniência armazenados;

- **Browser de Proveniência**: Oferece uma visualização interativa dos dados de proveniência;

- **Gerador de Grafo de Proveniência**: Exporta os dados de proveniência como imagens estáticas de grafos, representando as relações de derivação.

# Modelagem dos dados

A ProvInCiA modela os dados de proveniência utilizando os conceitos do W3C PROV, os quais são: 

- **Entidades**: Artefatos transformados (e.g., vídeos, datasets, imagens);

- **Atividades**: Processos ou ações que geram, modificam ou consomem entidades (e.g., script de processamento de imagens);

- **Agentes**: Responsáveis diretos ou indiretos pelas atividades (e.g., indivíduos, organizações, sistemas);

Distingue também entre **proveniência prospectiva (p-prov)**, que descreve a estrutura lógica do dataflow (o "que se espera"), e **proveniência retrospectiva (r-prov)**, que registra a execução concreta de um dataflow (o "que realmente aconteceu"), sendo esta última crucial para auditoria.

# Estudo de caso

A eficácia da ProvInCiA foi avaliada em um **estudo de caso real de monitoramento de alagamentos** em uma aplicação de CI. Essa aplicação envolvia quatro dataflows independentes que, combinados, formavam um meta-dataflow (captura de vídeos, pré-processamento de frames, treinamento de modelos de aprendizado de máquina, e sistema de monitoramento automatizado). Foram executadas **consultas de proveniência (Q1 a Q4)**, desenvolvidas em conjunto com especialistas da Defesa Civil de Niterói, para demonstrar a capacidade da ProvInCiA de rastrear informações críticas:

- **Q1**: Identificar o vídeo de origem de um frame específico (essencial para conformidade legal e ética);
- **Q2**: Atribuir a responsabilidade de uma extração de frames a um usuário em uma data/hora específica;
- **Q3**: Listar tarefas de treinamento de modelo executadas por um usuário (importante para auditoria e qualidade do modelo);
- **Q4**: Rastrear todos os vídeos utilizados para treinar um modelo de detecção de alagamentos (crucial para validar e auditar o sistema em caso de mau desempenho).

# Meta futura

Como trabalho futuro, planeja-se estender o framework para **gerenciar dependências assíncronas acionadas por eventos** e incorporar uma **camada Text-to-SQL**, capaz de converter consultas em linguagem natural para SQL utilizando LLM.

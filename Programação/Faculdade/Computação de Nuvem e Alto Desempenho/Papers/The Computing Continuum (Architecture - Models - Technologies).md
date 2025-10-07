### Glossário:

**Mobile Cloud Computing (MCC):**

> O Mobile Cloud Computing (MCC), conforme abordado no _paper_, refere-se à **execução de aplicações móveis utilizando recursos de computação em nuvem**. Nesse modelo, os dispositivos móveis funcionam como clientes que se conectam a servidores remotos na nuvem através da internet. O MCC é definido como um **modelo para o aumento elástico das capacidades de dispositivos móveis através de acesso sem fio ubíquo a recursos de armazenamento e computação em nuvem**, com adaptação dinâmica e consciente do contexto às mudanças no ambiente operacional.

**Objetivos do MCC:**

O principal objetivo do MCC é **resolver problemas inerentes aos dispositivos móveis**, como:

• Limitação de recursos;

• Baixa conectividade;

• Alto consumo de energia.

**Características do MCC:**

Características do MCC destacadas no _paper_ incluem:

• **Implantação**: Distribuída.

• **Consciência de localização (****Location awareness****)**: Consciente.

• **Recursos físicos**: Limitados (referindo-se aos dispositivos móveis clientes).

• **Distância à fonte de dados**: Muito próxima (em relação ao dispositivo móvel, que é o cliente).

• **Tempo de resposta**: Muito rápido.

**Edge-computing:**

> O _Edge Computing_ (EC) é um **modelo descentralizado** que tem como objetivo **levar as capacidades de processamento, armazenamento e rede para a borda da rede**. Ele atua como uma **camada intermediária entre a camada de** **endpoints** **(IoT) e a camada da nuvem**.

**Motivos para a criação:**

O surgimento do _Edge Computing_ foi motivado pela necessidade de **superar as limitações do** **cloud computing** **tradicional** para as aplicações cada vez mais sofisticadas da IoT. Essas limitações incluem:

• **Latência excessiva**.

• **Gargalos de rede e congestionamento**.

• **Problemas de largura de banda** ao mover grandes volumes de dados da borda da rede para centros de dados remotos na nuvem.

**Características:**

• **Implantação**: Distribuída.

• **Consciência de localização (****Location awareness****)**: Consciente.

• **Recursos físicos**: Limitados em comparação com a nuvem, mas mais poderosos que os dispositivos de _endpoint_.

• **Distância à fonte de dados**: Próxima.

• **Tempo de resposta**: Muito rápido.

> No contexto do _computing continuum_, o _Edge Computing_ é uma das **três camadas principais**, juntamente com a camada _endpoint_ (IoT) e a camada da nuvem. A integração dessas camadas permite um **gerenciamento de dados eficiente e em tempo real**, combinando a escalabilidade da nuvem com a baixa latência e a computação que preserva a privacidade da borda. Os nós de borda podem ser qualquer dispositivo com poder de computação e são conectados aos centros de dados da nuvem.

**Continuum Computing**

> O _computing continuum_ é um paradigma que **integra, organiza e considera os recursos de computação e rede em diferentes infraestruturas para implantar cargas de trabalho, em vez de depender de uma infraestrutura específica**. Ele busca alavancar e integrar recursos em diferentes camadas (como IoT, _edge_ e nuvem) para formar um sistema unificado.

**Camadas:**

**Camada de Endpoint ou IoT:** 

> Inclui objetos ou "coisas" ao nosso redor, como sensores, câmeras e dispositivos móveis. Eles são conectados à rede _edge_ e, possivelmente, uns aos outros, por conexões com ou sem fio.

**Camada Edge**: 

>  Combina nós _edge_, que podem ser qualquer dispositivo equipado com poder de computação. Esta camada está conectada aos centros de dados da nuvem.

**Camada da Nuvem (***Cloud****)**: 

> Consiste em grandes centros de dados pertencentes a provedores de serviços em nuvem. Esses centros de dados são locais físicos para armazenar ou processar dados, utilizando suas infraestruturas de computação, armazenamento e rede.

A integração dessas camadas permite um **gerenciamento de dados eficiente e em tempo real** para diversas aplicações e casos de uso. Isso combina a infraestrutura de **alta performance, escalável e de alta confiabilidade** da nuvem com a **baixa latência e a computação que preserva a privacidade** da camada _edge_.

**Fog Computing:**

> Semelhante ao _Edge Computing_, também é um modelo descentralizado que move os recursos da nuvem para mais perto dos usuários. Os nós _fog_ são extensões da nuvem e podem existir em camadas hierárquicas, permitindo balanceamento de carga e transferência de dados entre nós. Há uma diferença sutil: os nós _fog_ são considerados infraestruturas estendidas em uma nuvem híbrida, enquanto dispositivos _edge_ podem ou não envolver a nuvem no processamento/armazenamento.

**Multi-Access Edge Computing (MEC):**

> Padronizado pelo ETSI, o MEC combina serviços de TI com capacidades de _cloud computing_ na borda da rede móvel para reduzir a latência e melhorar a experiência do usuário. É uma tecnologia-chave para redes 5G e além, suportando serviços como jogos e realidade aumentada.

### Qual o trabalho?

O artigo **"The computing continuum: From IoT to the cloud"** oferece uma visão abrangente da evolução da computação, focando na integração de **IoT, edge e cloud computing** para formar um **continuum computacional**. Ele explora as limitações da computação em nuvem tradicional, como latência e largura de banda, e apresenta modelos emergentes como **Mobile Cloud Computing, Edge Computing e Fog Computing** como soluções. A pesquisa propõe **arquiteturas de referência para computação e comunicação**, detalhando seus componentes e funcionalidades em cada camada. Além disso, o trabalho valida essas arquiteturas através de diversos **casos de uso em setores como ciência, indústria, saúde, consumo, governança e municípios**, e discute **tendências futuras e direções de pesquisa** para otimizar o continuum computacional em termos arquitetônicos, tecnológicos, conceituais e infraestruturas.
### Quem é o autor?

Os autores do artigo são:

• **Auday Al-Dulaimy**

• **Matthijs Jansen**

• **Bjarne Johansson**

• **Animesh Trivedi**

• **Alexandru Iosup**

• **Mohammad Ashjaei**

• **Antonino Galletta**

• **Dragi Kimovski**

• **Radu Prodan**

• **Konstantinos Tserpes**

• **George Kousiouris**

• **Chris Giannakos**

• **Ivona Brandic**

• **Nawfal Ali**

• **André B. Bondi**

• **Alessandro V. Papadopoulos**

### Quais contribuições foram feitas?

• **Discussão da Evolução dos Modelos de Computação**

> O artigo discute a evolução dos modelos de computação em direção ao paradigma do **continuum de computação**, com foco na computação em nuvem como o modelo _De Facto_ que oferece escalabilidade, flexibilidade, custo-benefício, sustentabilidade ambiental e vantagem competitiva. Ele também ilustra as limitações da computação em nuvem que impulsionaram a necessidade de novos modelos de computação.

• **Proposta de Novas Arquiteturas de Referência**

> O trabalho lista os modelos de computação que formam o continuum de computação e as tecnologias de comunicação que os suportam. Propõe **duas novas arquiteturas de referência**: uma arquitetura de referência de computação para cobrir cada modelo de computação _edge-cloud_ e uma arquitetura de referência de comunicação para as tecnologias de comunicação _edge-cloud_. O artigo demonstra como essas arquiteturas de referência podem ser usadas para explorar _trade-offs_ de design para implantações de aplicativos no continuum de computação.

• **Design e Demonstração de Casos de Uso Reais**

> Foram projetados e demonstrados vários casos de uso reais de diferentes setores, como indústria, ciência e saúde. Estes casos de uso são novos, criados pelos autores, e servem para validar as arquiteturas de referência propostas, mostrando como suas camadas de implementação são mapeadas para a descrição do continuum de computação. Além disso, o trabalho seleciona e apresenta algumas tendências atuais relacionadas à nuvem e sua importância para diversos setores.

• **Identificação de Desafios e Limitações**

> O artigo destaca os desafios e limitações de diferentes modelos de computação e do próprio continuum de computação. Isso visa fornecer _insights_ sobre as restrições desses modelos e seu impacto nos sistemas de computação em geral.

• **Visão dos Autores para o Futuro do Continuum de Computação**

> O trabalho apresenta a visão dos autores sobre o futuro do continuum de computação. Essa visão prevê que aplicativos e casos de uso evoluirão para usos mais sofisticados com requisitos mais complexos, incluindo recursos de computação e níveis de desempenho. Consequentemente, o continuum de computação precisará continuar a evoluir para atender a esses requisitos. Para isso, o a
> artigo define diferentes direções de pesquisa a serem investigadas para um continuum de computação mais eficiente e unificado, ao mesmo tempo em que atende aos requisitos dos aplicativos.

### Qual a estratégia utilizada na abordagem?

As estratégias utilizadas na abordagem do estudo podem ser resumidas da seguinte forma:

**Análise e Discussão da Evolução dos Modelos de Computação**

> O estudo discute a evolução dos modelos de computação, com um foco particular na computação em nuvem como o modelo _De Facto_, e explora suas limitações que impulsionaram o surgimento de novos modelos.

**Definição Abrangente do Continuum de Computação** 

> Propõe uma nova definição para o "continuum de computação" como o paradigma que integra, organiza e considera os recursos de computação e rede em diversas infraestruturas (dispositivos _endpoint_, nós de _edge_, centros de dados em nuvem e as redes que os conectam) para a implantação de cargas de trabalho, em vez de depender de uma infraestrutura específica.

**Proposição de Novas Arquiteturas de Referência**:

    ◦ Desenvolve **duas novas arquiteturas de referência**: uma para os modelos de computação _edge-cloud_ (Endpoint, Edge e Cloud) e outra para as tecnologias de comunicação _edge-cloud_.

    ◦ A arquitetura de computação unificada para modelos de computação além da nuvem é construída sintetizando características compartilhadas por modelos como Mobile Cloud Computing (MCC), Edge Computing (EC), Fog Computing (FC) e Multi-Access Edge Computing (MEC).

    ◦ A arquitetura de comunicação propõe uma estrutura recomendada e independente de tecnologia para todas as aplicações de IoT, mapeando diferentes tecnologias relacionadas à comunicação no continuum IoT–_edge_–nuvem.

**Validação Através de Casos de Uso Reais**

    ◦ Desenvolve e demonstra **vários casos de uso reais** de diferentes setores (como indústria, ciência, saúde, consumo, governança e municípios) para validar as arquiteturas de referência propostas.

    ◦ Esses casos de uso são inéditos, criados pelos autores, e servem para mostrar como suas camadas de implementação são mapeadas para a descrição do continuum de computação. A validação da arquitetura de referência de computação foi realizada através de uma prova de conceito experimental numérica em trabalho anterior.

**Revisão e Comparação Abrangente da Literatura** 

> O estudo realiza uma revisão de trabalhos relacionados que abordam computação em nuvem e modelos emergentes, mas ressalta que esses trabalhos não aprofundam as questões de pesquisa no continuum de computação ou não fornecem arquiteturas de referência para modelos computacionais e tecnologias de comunicação, nem validam casos de uso com arquiteturas.

**Identificação de Desafios e Tendências Futuras**

> Destaca os desafios e limitações de diferentes modelos de computação e do próprio continuum de computação. Além disso, apresenta a visão dos autores sobre o futuro do continuum de computação, definindo direções de pesquisa para um continuum mais eficiente e unificado.

**Análise de Perspectivas Múltiplas** 

> O trabalho aborda o continuum de computação tanto do ponto de vista da **computação** quanto da **comunicação**, fornecendo um modelo para a execução de diversas aplicações.

### Qual lacuna ou problema está tentando resolver?

**Limitações do Cloud Computing para Aplicações IoT Avançadas** 

> As aplicações na era da revolução IoT estão se tornando cada vez mais sofisticadas, com requisitos funcionais e não funcionais diversos, incluindo recursos de computação e níveis de desempenho. Embora o _cloud computing_ seja um grande facilitador, suas limitações o tornam **inadequado para atender a todos os objetivos de design de novas aplicações e casos de uso**. As limitações incluem:

    ◦ **Problemas de Conectividade, Largura de Banda e Latência**: As localizações remotas dos centros de dados da nuvem exigem transmissão de dados com dispositivos IoT, o que pode resultar em gargalos de rede, congestionamento intensivo e problemas de latência. Isso afeta negativamente aplicações que exigem tempo de reação curto ou dependem de conexões estáveis.

    ◦ **Gerenciamento Centralizado**: O _cloud computing_ clássico oferece operações centralizadas e não suporta serviços localizados, o que entra em conflito com os requisitos de muitas aplicações e casos de uso.

    ◦ **Aspectos de Segurança e Privacidade**: A segurança dos dados é uma preocupação importante devido ao armazenamento centralizado e ao compartilhamento de recursos entre múltiplos usuários.

    ◦ **Design de Aplicações**: O _cloud computing_ é melhor explorado por aplicações projetadas com considerações arquitetônicas nativas da nuvem, sendo um desafio para outras aplicações lidar com as demandas dinâmicas.

    ◦ O _paper_ resume estes desafios em diversas categorias como Desempenho, Confiabilidade, Disponibilidade, Escalabilidade, Sustentabilidade, Elasticidade, Gerenciamento de Energia, Gerenciamento de Virtualização, Provisionamento Automatizado de Serviços, Gerenciamento de Tráfego, Gerenciamento de Dados, Latência, Conscientização de Localização, Segurança, Privacidade, Confiança, Responsabilidade, Novas Arquiteturas de Nuvem e Engenharia de Aplicações para a Nuvem.

**Necessidade de Integração de Camadas (Computing Continuum)**

> Para superar as limitações do _cloud computing_, é necessária a integração de recursos em diferentes camadas (como IoT, _edge_ e nuvem) para formar e utilizar um **contínuo de computação**. No entanto, essa integração, embora ofereça serviços inovadores, introduz novos desafios (por exemplo, monitoramento de desempenho e garantia de segurança) que precisam ser investigados. Há uma necessidade de entender como habilitar e utilizar eficientemente as camadas e componentes do _computing continuum_, como novos modelos de computação podem ser integrados e quais direções potenciais podem aprimorar a funcionalidade e o desempenho.

**Falta de uma Definição Universalmente Aceita para o Computing Continuum** 

> Dada a ausência de uma definição universalmente aceita para o _computing continuum_, o _paper_ propõe uma nova definição: "O _computing continuum_ é o paradigma que integra, organiza e considera os recursos de computação e rede em diferentes infraestruturas (dispositivos de _endpoint_, nós de _edge_, centros de dados de nuvem e as redes que os conectam) para implantar cargas de trabalho, em vez de depender de uma infraestrutura específica".

**Ausência de Arquiteturas de Referência Abrangentes** 

> O trabalho identifica uma lacuna significativa na literatura, afirmando que **nenhum trabalho anterior forneceu arquiteturas de referência para o modelo computacional e as tecnologias de comunicação no** **computing continuum**. Para preencher essa lacuna, o _paper_ apresenta **duas novas arquiteturas de referência**: uma para modelos de computação _edge-cloud_ e outra para tecnologias de comunicação _edge-cloud_.

**Falta de Validação de Arquiteturas através de Casos de Uso Diversos** 

> Trabalhos anteriores não apresentam casos de uso de diferentes domínios de aplicação enquanto os relacionam às arquiteturas de referência para validá-los. O _paper_ aborda isso projetando e demonstrando vários casos de uso reais de diferentes setores (como indústria e ciência) para validar as arquiteturas de referência propostas.

### Qual a aplicabilidade prática ou teorica dessa pesquisa?
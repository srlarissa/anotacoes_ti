## Definição

Modelo conceitual de dados que representa as informações de um domínio por meio de **entidades**, seus **atributos** e os **relacionamentos** entre elas.

### Entidade

> Representados por um retângulo, é o conjunto de objetos da realidade modelada, os quais deseja-se manter as informações no banco de dados. Ou seja, é uma coisa ou pessoa, concreta ou abstrata, que pode ser individualmente identificado.

### Atributo

> Representados pelos círculos e são o dado ou informação que é associado a cada ocorrência de uma entidade ou relacionamento, sendo propriedades ou características de relevância. O **valor** de um atributo se refere ao valor que ele possui naquele momento. Já o **domínio** indica as restrições de integridade e a descrição da classe de valores, logo, este representa todos os valores que um determinado atributo pode ter. A cardinalidade em atributos mínimos e máximos, os quais indicam, respectivamente, se o atributo é obrigatório ou opcional (1 ou 0), e se o atributo é mono ou multi valorado (1 ou n). Alguns atributos também podem ser compostos (como endereços, por exemplo) ou elementares. Se o atributo for **monovalorado**, **obrigatório** e elementar então nada precisa ser anotado no atributo.

### Relacionamento

> Representados pelos losangos, são uma correspondência entre duas ou mais entidades (não necessariamente distintas), na qual cada entidade desempenha um papel no relacionamento. Então, podemos concluir que relacionamentos é um conjunto de associações entre entidades sobre as quais deseja-se manter informações na base de dados. Relacionamentos não são aleatórios, seguem as regras de organização e o modelo de negócio.

### Relacionamento Identificador

> Tipo de relacionamento necessário para identificar uma ou mais instâncias de determinada entidade. Esta entidade que necessita do relacionamento para existir e ser identificada é chamada **entidade fraca**.

### Cardinalidade

> Propriedade dos relacionamentos, o qual indica o número de ocorrências de uma entidade que podem estar associadas a uma determinada ocorrência de entidades através do relacionamento. Anotamos sempre duas cardinalidade em um relacionamento entre entidades: mínima e máxima.






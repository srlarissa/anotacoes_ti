# Definição

> Representados por um retângulo, é o conjunto de objetos da realidade modelada, os quais deseja-se manter as informações no banco de dados. Ou seja, é  uma coisa ou pessoa, concreta ou abstrata, que pode ser individualmente identificado. 

# Especialização

> Por vezes, será necessário derivar uma entidade com outras, mais específicas, ditas especializadas. A especialização é representada pelo triângulo, referenciado a herança de entidades filhas em relação à uma entidade mãe.

**Nota:** Ainda que seja possível heranças múltiplas, somente é possível se a raiz for unitária.


Sempre que uma entidade for especializada, pode ser feito de duas formas quanto sua representação:

- **t:** Total, quando todo o espectro possível daquela entidade for representada na especialização;
- **p:** Quando nem todos os tipos de entidades forem representadas em uma especialização uma vez que a entidade mãe é suficiente para representar as demais instâncias.

Há também representações relacionadas a recorrência de especializações:

- **x:** Exclusiva, logo, uma instância apenas poderá ter uma especialização;
- **c:** Compartilhado, que ocorre quando uma instância pode ter mais de uma especialização.

Portanto, podemos concluir que:

- **ct:** Todas as especializações foram representadas e uma instância pode ter múltiplas especializações;
- **cp:** Quando nem todas as especializações foram representadas e uma mesma instância poderá ter múltiplas especializações;
- **xt:** Quando todas as especializações forem representadas e cada instância poderá ter apenas uma especialização;
- **xp:** Que nem todas as especializações foram representadas e uma instância poderá ter apenas uma especialização.


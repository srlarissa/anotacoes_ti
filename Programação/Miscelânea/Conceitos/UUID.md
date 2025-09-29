> É um identificador único universal (Universally Unique Identifier), assim sendo, as probabilidades de repetição são extremamente baixas. É composto por uma sequência de 128 bits *(16bytes)*, e é muito utilizado em banco de dados ou outras aplicações que necessitem de formas para identificar registros de forma única, sem depender de autoincremento ou sequências.

## Anatomia

Geralmente é representado por um formato hexadecimal com hifens:

```java
550e8400-e29b-41d4-a716-446655440000
```

Como pode ser gerado localmente, não há a necessidade de um banco de dados para gera-lo. Muito utilizado em sistemas distribuídos, já que várias instâncias podem criar registros ao mesmo tempo sem risco de colisão entre as chaves.



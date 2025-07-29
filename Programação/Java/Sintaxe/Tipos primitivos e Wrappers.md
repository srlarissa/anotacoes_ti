Enquanto os [[Tipos primitivos.canvas|Tipos primitivos]] são o dado base, instâncias de [[Classe wrapper.canvas|Classe wrapper]]  são objetos que encapsulam esses tipos primitivos.

# 1. String, StringBuilder e StringBuffer

Cada um dos três tipos é melhor adaptado para um cenários específico:

## String:

É **imutável**, portanto, sempre que uma concatenação é feita, o valor atual contido na variável é armazenado em memória e uma nova instância de String é gerada para armazenar o valor atual e o concatenado. Dessa forma, concatenações *(principalmente em grandes volumes)* podem levar a perda de desempenho.

## StringBuilder:

Uma classe mutável, adaptada para concatenações em loop, mas melhor otimizada para cenários **single-thread**, uma vez que não é thread-safe.

## StringBuffer: 

Semelhante ao anterior, é um objeto mutável, adaptado para concatenações em loop, sanando o gargalo de funcionamento em ambientes **multi-thread**. Porém, há uma pequena perda em desempenho em relação ao StringBuilder devido à sincronização.

# 2. BigDecimal


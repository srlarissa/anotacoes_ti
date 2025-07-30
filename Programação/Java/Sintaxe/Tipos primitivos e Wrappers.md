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

Os tipos primitivos double e float tem precisão de 7 e 15 casas decimais respectivamente, dessa forma, por muitas vezes, contas aritméticas entre valores desse tipo tem resultado impreciso pela natureza de como essas operações são feitas:

```java

System.out.println(0.1 + 0.2); // saída: 0.30000000000000004

```

Os tipos double e float executam suas operações convertendo os valores decimais representados em binários e depois novamente convertidos para a base decimal novamente. Dessa forma, a precisão por vezes é perdida nesse processo. Para sanar esse problema, a Classe BigDecimal é utilizada para manutenção da precisão apesar da perda na velocidade do processamento. Como a Classe String, BigDecimal é imutável, sendo assim, ao ser feita uma operação é necessário desembrulhar o conteúdo e consumi-lo.

```java
BigDecimal a = new BigDecimal("0.1");
BigDecimal b = new BigDecimal("0.2");
System.out.println(a.add(b)); // saída: 0.3
```

# 3. Optional

Visando evitar erros em tempo de execução por conta do valor contido em um objeto ser null *(NullPointerException)*, a classe contêiner Optional foi criada.

```java
String nome = obterNome(); 
System.out.println(nome.length()); // ← Pode lançar NullPointerException!
```

Assim, é possível criar validações, verificando se um determinado objeto está vazio ou não antes de tentarmos acessa-lo.

```java
Optional<String> nomeVazio = Optional.empty();

if (nomeVazio.isPresent()) {
    System.out.println(nomeVazio.get());
} else {
    System.out.println("Nome não disponível.");
}
```

|Método|Explicação|
|---|---|
|`Optional.of(valor)`|Cria um Optional com valor (erro se for `null`)|
|`Optional.ofNullable(valor)`|Cria com valor ou vazio (`null` vira `Optional.empty()`)|
|`Optional.empty()`|Cria um Optional vazio|
|`isPresent()` / `isEmpty()`|Verifica se há valor|
|`get()`|Retorna o valor, **mas lança exceção se vazio**|
|`orElse(valor)`|Retorna o valor, ou outro se estiver vazio|
|`orElseGet(Supplier)`|Igual ao `orElse`, mas com `Supplier` (lazy)|
|`ifPresent(Consumer)`|Executa uma ação se o valor estiver presente|
|`map(Function)`|Transforma o valor contido, se presente|

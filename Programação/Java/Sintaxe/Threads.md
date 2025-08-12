
**Definição:** São linhas de execução independentes dentro de uma aplicação. Dessa forma, podemos criar algoritmos que funcionem em uma ou múltiplas threads. 

# Single-thread

**Definição:** Quando uma lógica executa inteiramente em uma única thread, chamamos single-thread *(normalmente a main)*. Assim, cada linha de código é executada por vez, não havendo riscos de concorrência ou conflito de acesso a partes do código. *(Região Crítica)* 

```java
System.out.println("A");
System.out.println("B");
```

# Multi-thread

**Definição:** Ambiente onde múltiplas threads executam em paralelo ou simultaneamente., permitindo que várias tarefas sejam executadas ao mesmo tempo. Quando as tarefas são muito intensas *(como webservers, cálculos extensos, requisições paralelas)*, o uso de ambientes multi-threads pode trazer mais performance. 

Por exemplo, abaixo a variável valor é comum dentro da classe. Assim, caso o método incrementar for chamado em um ambiente multi-thread poderá ter um resultado não determinístico: duas threads podem tentar somar ao mesmo tempo e sobrescrever o valor uma da outra.
```java
class Contador {
    int valor = 0;

    public void incrementar() {
        valor++; // não é seguro se chamado por múltiplas threads
    }
}
```

Uma solução para o problema acima é o uso de [[AtomicInteger]].
```java
class Contador {
    private final AtomicInteger valor = new AtomicInteger(0);

    public void incrementar() {
        valor.incrementAndGet(); // thread-safe
    }
}
```

Outra forma de lidar com o problema da condição de corrida é utilizando blocos ```synchronized```, garantindo assim exclusão mútua ao utilizar recursos compartilhados. Existem duas formas de utilizar:

```java
public void incrementar() {
    synchronized (this) {
        contador++;
    }
}

public synchronized void incrementar() {
    contador++;
}
```

**Obs:** É exigido cuidado com a sincronização, uma vez que o uso de multi-thread pode gerar condição de corrida *(modificar os mesmos dados ao mesmo tempo)*. Não apenas isso, nem todos os casos o uso de multi-thread trará mais performance, e, se utilizado levianamente, poderá ter o efeito oposto. 


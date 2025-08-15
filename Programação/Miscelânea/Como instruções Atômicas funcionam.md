
Como verificamos no meu post anterior a respeito de ambientes multi-thread (https://sl1nk.com/mais-contexto-sobre-aplicacoes-multi-thread), apesar de contador++ parecer uma operação simples e segura, ela pode nos colocar em condição de corrida (race condition). Para entender melhor o porque, começaremos compreendendo a diferença entre atribuir valor a uma variável atômica e não-atômica.

```java
public class CondicaoDeCorrida {

    private static int contador = 0; // Recurso compartilhado

    public static void main(String[] args) throws InterruptedException {
        // Thread 1 incrementa 1000 vezes
        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                contador++; // NÃO É ATÔMICO!
            }
        });

        // Thread 2 incrementa 1000 vezes
        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                contador++; // Mesmo recurso compartilhado
            }
        });

        // Iniciar as threads
        t1.start();
        t2.start();

        // Esperar as duas terminarem
        t1.join();
        t2.join();

        // Resultado final esperado: 2000
        System.out.println("Valor final do contador: " + contador);
    }
}
```

Como a atribuição de valor é feita?

No exemplo acima, temos o cálculo e atribuição feitos através da utilização do operador "++" no final da variável contador. O que, a primeira vista, pode parecer enxuto o suficiente, mas vamos olhar mais de perto o que de fato está acontecendo por baixo dos panos:

1. Uma copia do valor atual de contador é enviado para uma memória temporária na CPU chamada "registrador", a qual ficará responsável pela operação aritmética;
2. No registrador, esse valor é incrementado em 1 para que a instrução "++" seja cumprida adequadamente;
3. O novo valor é escrito de volta no endereço de memória onde a variável contador está alocada, substituindo o valor anterior.

Ou, em código, podemos interpretar da seguinte forma para melhor compreensão:

```java
int temp = contador;
temp = temp + 1;
contador = temp;
```

Como podemos verificar, um longo processo acontece até finalmente a instrução ser efetivamente executada, portanto, nesse meio tempo, outras threads podem conseguir acessar a variável contador, abrindo precedentes para o resultado obtido em alguma das operações estar equivocado (logo, não determinístico).

Como operações Atômicas auxiliam a resolver esse problema?

Revisando o que vimos anteriormente, a operação "++" é composta de essencialmente três etapas:

1. Ler o valor da variável contador;
2. Incrementar esse valor;
3. Escrever o novo valor de volta na variável após acessar o endereço de memória correto.

Quando declaramos um inteiro utilizando AtomicInteger, por exemplo, utilizamos uma técnica chamada de CAS (compare and swap, ou, comparar e trocar), as quais operam utilizando instruções de baixo nível (instruções de hardware) que são atômicas por natureza:

1. O valor atual de contador é lido e enviado para o registrador;
2. Se ninguém tiver alterado o valor da variável contador nesse percurso, a operação segue normalmente. Caso contrário, a operação é cancelada e recomeça;
3. A operação "++" e a reescrita do valor novo em contador ocorre como um único bloco (atômico), garantindo que nenhuma outra thread interfira em sua modificação.

Abaixo a mesma classe CondicaoDeCorrida, agora thread-safe graças ao uso de AtomicInteger:

```java
import java.util.concurrent.atomic.AtomicInteger;

public class CondicaoDeCorrida {

    private static AtomicInteger contador = new AtomicInteger(0); // Recurso compartilhado atômico

    public static void main(String[] args) throws InterruptedException {
        // Thread 1 incrementa 1000 vezes
        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                contador.incrementAndGet(); // método para incremento atômico
            }
        });

        // Thread 2 incrementa 1000 vezes
        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                contador.incrementAndGet(); // método para incremento atômico
            }
        });

        // Iniciar as threads
        t1.start();
        t2.start();

        // Esperar as duas terminarem
        t1.join();
        t2.join();

        // Resultado final esperado: 2000
        System.out.println("Valor final do contador: " + contador.get());
    }
}
```

E é isso o que significa utilizar instruções atômicas, tudo é feito em blocos únicos e indivisíveis garantindo que a variável compartilhada tenha integridade durante todo o processo.

A seguir, deixo a documentação do pacote java.util.concurrent.atomic pela Oracle caso queiram explorar mais o tópico:

https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/atomic/package-summary.html

Bons estudos!










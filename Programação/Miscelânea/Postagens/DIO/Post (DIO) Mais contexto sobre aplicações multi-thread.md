
Para entender melhor o que está acontecendo quando utilizamos uma aplicação multi-thread, temos que primeiro entender alguns conceitos:

O que é Condição de corrida? 

Quando criamos um algoritmo, a ordem que será executada cada uma das instruções é importante para que obtenhamos o resultado desejado. Dessa forma, a condição de corrida, como o nome sugere, ocorre quando duas threads desejam acessar o mesmo recurso compartilhado (o que pode ser uma variável, por exemplo) em simultâneo. Assim, a velocidade na execução de cada código é o que determinaria o resultado obtido pela utilização do método. Exemplo:

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

Embora na maioria das vezes o resultado retornado seja 2000, isso não é garantido! O que, em uma situação no mundo real, pode acarretar problemas sérios. 

O que é Exclusão Mútua?

Até existem recursos compartilhados que precisam ser acessados ainda que em simultâneo por todos os que necessitarem, mas nem sempre este é o caso. Como no exemplo acima, muitos recursos compartilhados têm seu resultado final comprometido caso mais de uma thread tenha acesso a ele por vez. O conceito de garantir exclusividade no acesso a uma Região Crítica é chamado Exclusão Mútua.

Vamos considerar que uma thread é como uma avenida onde passam múltiplos carros. Caso o fluxo fique muito intenso, a construção de mais avenidas paralelas seria uma solução válida para a melhoria no trânsito da região. É exatamente isso que está sendo feito quando criamos um ambiente multi-thread. 

A grosso modo, podemos dizer que, se a máquina executando a aplicação tem mais de um núcleo de processador, esse ambiente multi-thread permite execuções em paralelo para cada uma de suas threads (limitada ao número de núcleos, é claro). Caso a máquina não tenha vários núcleos, na prática, o que ocorre é que o processador está alternando entre cada uma das threads muito rápido, de forma que, para o usuário, parece que tudo ocorre em paralelo, tamanha é a velocidade dessas alternâncias!

Assim, ter estratégias para garantir que apenas uma thread possa acessar um recurso compartilhado por vez (Exclusão Mútua), como o uso de classes que permitem uso de métodos atômicos (como AtomicInteger) ou o uso adequado de synchronized, é essencial para garantirmos que o nosso algoritmo esteja funcionando de forma determinística (ou seja, que tenha resultados previsíveis).




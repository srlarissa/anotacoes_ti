São interfaces que contém apenas um único método abstrato, muito utilizadas para chamadas de API, ouvintes de eventos, execução de tarefas (como com Runnable ou Callable) ou operações assíncronas. Como qualquer interface, aceita atributos mas estes são final

```java

@FunctionalInterface
public interface Operacao {
    int executar(int a, int b);
}

Operacao soma = (a, b) -> a + b;
System.out.println(soma.executar(3, 4)); // saída: 7

```


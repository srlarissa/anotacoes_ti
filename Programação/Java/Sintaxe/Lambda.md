A forma mais moderna e menos verbosa de criar funções anônimas em Java através da  [[Interface Funcional]] Runnable. Dessa forma, é possível passar callbacks ou armazena-las dentro de variáveis, sendo uma das poucas formas de transformar uma função em um valor.

```java

Runnable tarefa = () -> System.out.println("Executando...");

```




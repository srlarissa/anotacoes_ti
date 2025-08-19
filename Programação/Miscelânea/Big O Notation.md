Você conhece a notação Big-O?

Existem diversas formas de decidir qual estrutura de dado ou qual laço de repetição é mais adequado para o algoritmo de sua aplicação. Uma delas é a notação Big-O. Mas quais os insights que essa ferramenta pode realmente nos oferecer?

Inicialmente, existem duas dimensões que podemos analisar para um cenário completo a respeito da projeção no crescimento de um algoritmo:

- Analise de Tempo: Mede o tempo de execução, ou seja, a execução de cada linha de código do bloco;
- Analise de Espaço: Mede o quanto de memória é gasta para a execução.

E, essas analises, podem ser categorizadas em nas seguintes denominações:

- O(1): Tempo ou Espaço de acesso constante;
- O(log n): cresce devagar e divide o problema recursivamente(ou seja, a cada passo do processo, o problema é dividido a uma certa fração do tamanho inicial);
- O(n): percorre todos os itens pelo menos uma vez;
- O(n log n): o problema é dividido pela metade recursivamente e percorre cada um dos itens pelo menos uma vez;
- O(n^2): todos contra todos.

Nota: Vale salientar que Big-O não analisa a performance de um código, e sim sua escalabidade. Exemplo:

```java

```




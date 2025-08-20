Você conhece a notação Big-O?

Existem diversas formas de decidir qual estrutura de dado ou laço de repetição é o mais adequado para o código de sua aplicação. Uma delas é a notação Big-O. Mas quais os insights que essa ferramenta pode realmente nos oferecer?

Inicialmente, existem duas dimensões que podemos analisar para um cenário completo a respeito da projeção no crescimento de um algoritmo:

- Analise de Tempo: Mede o tempo de execução, ou seja, a execução de cada linha de código do bloco;
- Analise de Espaço: Mede o quanto de memória é gasta para a execução.

E, essas analises, podem ser categorizadas em nas seguintes denominações:

- O(1): Tempo ou Espaço constante;
- O(log n): cresce devagar e divide o problema recursivamente(ou seja, a cada passo do processo, o problema é dividido a uma certa fração do tamanho inicial);
- O(n): percorre todos os itens pelo menos uma vez;
- O(n log n): O problema é dividido pela metade recursivamente e, em cada divisão, percorre cada um dos itens pelo menos uma vez;
- O(n²): Cada elemento deve ser iterado com todos os outros.

A relação entre cada uma das denominações está na imagem abaixo, sendo o mais próximo de O(N!) a pior e O(1) a mais desejável:

![[Pasted image 20250820113709.png]]

Nota: Vale salientar que Big-O não analisa a performance de um código, e sim sua escalabidade. Em resumo, O(1) não é constante porque seu valor é sempre igual, e, sim, porque ele não aumenta ou diminui de acordo com o tamanho do input. Veja o exemplo abaixo:

Pegaremos a problemática descrita no problema 242 do leetcode "Valid Anagram". (https://leetcode.com/problems/valid-anagram/)
Imaginemos que queremos criar um código que aceite como input duas strings e devolva um booleano sinalizando se ambas são anagramas ou não. Seguiremos duas abordagens para a resolução dessa questão:

Abordagem 1: 
Criamos dois métodos estáticos: 

1 - Transformamos cada uma das Strings em um array de char;

2 - Criamos um HashMap com um desses arrays, armazenando como chave a letra e como valor a frequência que esta letra aparece;

3 - Levando o HashMap criado no passo anterior em referencia, percorremos o outro array de char e, para cada letra que esteja contida no HashMap, decrementamos em um o valor

4 - Para finalizar, verificamos se todos os valores do HashMap são iguais a zero, indicando, assim, que todas as letras presentes na primeira string também estão presentes na segunda, apenas em ordem diferente.

```java
public class Main {  
    static Map<Character, Integer> charToMap(char[] word){  
        Map<Character, Integer> charCounter = new HashMap<>();  
  
        for (char c : word) {  
            if(!charCounter.containsKey(c)){  
                charCounter.put(c, 1);  
            }else{  
                int addCharacter = charCounter.get(c) + 1;  
                charCounter.put(c, addCharacter);  
            }  
        }  
        return charCounter;  
    }  
  
    static boolean anagramVerifier(Map<Character, Integer> firstWord, char[] secondWord){  
        for (char c : secondWord) {  
            if (!firstWord.containsKey(c)) return false;  
  
            int newValue = firstWord.get(c);  
            if(newValue == 0) return false;  
  
            firstWord.put(c, newValue - 1);  
        }  
        return firstWord.values().stream().noneMatch(v -> v != 0);  
    }  
  
    public static void main(String[] args){  
        String s = "anagram";  
        String t = "nagaram";  
  
        boolean result;  
  
        if(s.length() != t.length()){  
            result = false;  
        }else{  
            char[] sChars = s.toCharArray();  
            char[] tChars = t.toCharArray();  
  
            Map<Character, Integer> sCharMap = charToMap(sChars);  
  
            result = anagramVerifier(sCharMap, tChars);  
        }  
        System.out.println(result);  
    }  
}
```

Analisemos a complexidade do algoritmo acima passo a passo:

O método charToMap tem como complexidade média temporal é de O(n), uma vez que será necessário percorrer todas as letras de char[] para aloca-las adequadamente. O(1) para complexidade espacial já que o número máximo de caracteres é 26, logo, não importa o quanto a String cresça, o teto sempre será 26.

O método anagramVerifier tem complexidade temporal O(n) para a estrutura inicial que utiliza o for, já que é necessário passar por todas as letras de char[] e referenciar sua leitura no HashMap gerado. A verificação da existência de valores diferentes de zero tem complexidade O(1), uma vez que o acesso ao par chave-valor tem tempo constante e o uso de stream API também, e, não apenas isso, mas a verificação da presença de valores diferentes de zero também tem um número de tentativas constante (as 26 letras do alfabeto). A complexidade espacial, por outro lado, se mantém como O(1) para todos os casos.

No código, também, transformamos cada uma das String em um char[], o que tem complexidade O(n) , uma vez que o espaço reservado no array e o tempo percorrendo aumentam junto com a length da String inserida.

Em resumo, o algoritmo feito utilizando HashMap tem complexidade no pior dos casos O(n) para cada par de Strings.

Agora, vamos a segunda forma de resolver esse problema:

1 - Convertemos ambas String para char[];
2 - Usamos o método nativo para organizar arrays sort() para colocarmos ambos em ordem alfabética;
3 - Finalizamos comparando se os dois arrays são idênticos.

```java
public class Main {  
    public static void main(String[] args) {  
        String s = "anagram";  
        String t = "nagaram";  
        boolean isAnagram;  
  
        char[] sChars = s.toCharArray();  
        char[] tChars = t.toCharArray();  
  
        Arrays.sort(sChars);  
        Arrays.sort(tChars);  
  
        isAnagram = Arrays.equals(sChars, tChars);  
        System.out.println(isAnagram);  
  
    }  
}
```

Para a analise de complexidade:

Converter String para char[], como visto anteriormente, tem complexidade O(n) tanto em tempo quanto em espaço para cada uma das operações.

A operação sort(), tem em média complexidade temporal O(n log n) e, no pior dos casos, pode chegar a O(n²), uma vez que utiliza recursividade para reorganização dos itens em ordem crescente e complexidade espacial O(log n), também por conta da recursividade, pois precisa alocar um pouco mais de memória para empilhar e desempilhar os métodos durante sua execução.

Já a operação equals() tem complexidade temporal O(n), já que compara todos os itens no mesmo índice (ou seja, comparamos o índice zero de ambos, depois o índice 1, e assim sucessivamente), e complexidade espacial O(1) já que nenhum espaço extra precisa ser alocado para tal.


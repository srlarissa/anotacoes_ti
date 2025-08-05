
**Definição:** Transforma o ato de atribuir o valor uma variável do tipo integer em uma operação atômica. E, não apenas isso, essa classe oferece uma série de métodos igualmente atômicos para manuseio desse inteiro adicionado.
### Passos para atribuir um valor:

1. Ler o valor atual da variável;
2. Incrementar o valor atual;
3. Escrever o novo valor na variável.

Ou seja, o processo de atribuição de valor a um integer é composto de pelo menos três passos. Utilizando a classe AtomicInteger, essa operação ocorre em apenas um passo, tornando seu uso seguro em ambientes multi-thread.

```java
import java.util.concurrent.atomic.AtomicInteger;

public class ContadorSeguro {
    private AtomicInteger contador = new AtomicInteger(0);

    public void incrementar() {
        contador.incrementAndGet(); // incremento atômico
    }

    public int getValor() {
        return contador.get();
    }
}
```

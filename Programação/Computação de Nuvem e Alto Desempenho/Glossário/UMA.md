### Definição:

Composta por processadores idênticos com latência uniforme, ou seja, todos os processadores conseguem acessar qualquer endereço de memória em tempos iguais. m exemplo clássico é o **SMP (Symmetric MultiProcessor)**. Em um SMP, há um único espaço de endereçamento lógico e um mecanismo de hardware de memória centralizada. A memória é totalmente compartilhada, e há uma única cópia do Sistema Operacional, apresentando uma imagem única do sistema com excelente conectividade. No entanto, **não são escaláveis** para um grande número de processadores devido a limitações de barramento e largura de banda.

As limitações são principalmente físicas, como por exemplo:

- Barramento, multi-barramentos, crossbar switches, etc.;
- Limitações de escalabilidade;
- Limitações de largura da banda.

![[Pasted image 20250901162456.png]]
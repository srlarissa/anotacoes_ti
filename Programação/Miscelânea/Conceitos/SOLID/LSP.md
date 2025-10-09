## Definição:

> Objetos de uma classe derivada devem poder substituir objetos de sua classe base sem quebrar a aplicação.

## Conceitos chave:

- **Contrato/Interface:** Define o que é esperado;
- **Pré-condições:** O que deve ser verdade antes de usar;
- **Pós condições:** O que deve ser verdade após o uso;
- **Invariante:** O que deve sempre ser verdade;
- **Substitutibilidade:** Variações devem funcionar onde o tipo base funciona.

## Regras:

- Pré-condições não podem ser fortalecidas em subtipos;
- Pós condições não podem ser enfraquecidas em subtipos;
- Invariantes devem ser preservadas em subtipos;
- Exceções novas não devem ser lançadas em subtipos *(além das do tipo base)*.

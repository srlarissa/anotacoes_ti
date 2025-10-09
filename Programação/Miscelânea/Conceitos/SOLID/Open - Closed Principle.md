## Definição:

> Entidades de software *(classe, módulos, funções, componentes, etc.)* devem estar abertas para extensão e fechadas para modificação. O que significa dizer que: o código-fonte não deve ser alterado quando novos requisitos surgem, e sim, novas funcionalidades devem ser adicionadas através de extensão, como herança, composição ou outros.

## Motivos:

- Risco de quebrar funcionalidades existentes e introduzir bugs no código;
- Não ter a necessidade de um reteste completo;
- Ocorrência de violação de código já testado e estável e em produção;
- Dificuldade de manutenção, uma vez que o código crescerá desorganizadamente;
- Conflitos em equipe, uma vez que múltiplos desenvolvedores modificando o mesmo arquivo poderá causar inconsistências.


## Técnicas para aplicação:

- **Abstração:** Usar interfaces ou tipos abstratos;
- **Polimorfismo:** Diferentes implementações da mesma interface;
- **Composição:** Combinar objetos ao invés de modifica-los;
- **Injeção de dependências:** Passar comportamentos como parâmetros;
- **Padrões de projeto:** Strategy, Template Method, Decorator, etc.



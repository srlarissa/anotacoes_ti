## Definição:

> Um componente passa por etapas conhecidas como [ciclo de vida](obsidian://open?vault=anotacoes_ti&file=Programa%C3%A7%C3%A3o%2FMiscel%C3%A2nea%2FConceitos%2FCiclo%20de%20vida), e cada uma dessas etapas oferece um gancho ([hook](obsidian://open?vault=anotacoes_ti&file=Programa%C3%A7%C3%A3o%2FReact%2FGloss%C3%A1rio%2FHook)) no qual certos códigos poderão ser executados. 

## Estágios:

### Montagem (Mounting) - Nascimento

Quando um componente é inicializado, ele é criado e inserido no DOM, logo ele:

- Inicializa o estado;
- Faz as requisições iniciais;
- Configura os listeners.

### Atualização (Updating) - Vida

Quando props ou estado mudam, eles:

- Re-renderizam o componente;
- Atualiza o DOM;
- Reage as mudanças.

### Desmontagem (Unmounting) - Morte

Quando um componente é removido do DOM, ele:

- Limpa timers;
- Cancela requisições pendentes;
- Remove event listeners.

## Importância do Ciclo de Vida:

1. Evitar memory leak;
2. Otimizar performance;
3. Executar código no momento certo;
4. Gerenciar recursos adequadamente.


 






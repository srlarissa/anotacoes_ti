
## Definição:

> Serve para adicionar e gerenciar estados em um componente funcional.

## Anatomia:

> É formado por um array de duas posições na qual a primeira o valor é armazenado e a segunda contém uma função para atualizar o estado do valor armazenado na primeira.

### Exemplo:

```javascript
import { useState } from 'react';

function Contador() {
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>Você clicou {count} vezes</p>
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
  );
}
```

**Passo a passo**

1. Na primeira renderização, count receberá o valor 0;
2. Quando clicamos, setCount atualiza o estado do valor, nesse caso, somando em um o valor de count;
3. O React re-renderiza o componente com o novo valor.

## Inicialização:

Ao inicializar um useState, é possível definir um valor inicial contido na primeira posição do array

### Exemplo:

```javascript
const [nome, setNome] = useState('João');
const [idade, setIdade] = useState(25);
const [ativo, setAtivo] = useState(true);
const [itens, setItens] = useState([]);
const [usuario, setUsuario] = useState({ nome: '', email: '' });
```

Quando vamos executar um cálculo computacional caro ou demorado, há também a possibilidade de inicializar o valor utilizando o que chamamos de lazy inicialization. 

### Exemplo:

```javascript
// ❌ RUIM - processa array toda renderização
const [processados, setProcessados] = useState(
  dadosGrandes.map(item => processarItem(item))
);

// ✅ BOM - processa apenas uma vez
const [processados, setProcessados] = useState(() => 
  dadosGrandes.map(item => processarItem(item))
);
```

Desse modo, a função apenas é executada na primeira renderização, uma vez que quando o React recebe uma função com argumento, ele prontamente a executa ainda que não seja mais a primeira execução. Passando a função pesada como argumento de um lambda, é possível fazer com que a função que será prontamente executada seja a mesma, assim, a função pesada apenas será executada caso de fato seja a primeira execução. Via de regra, usaremos lazy initialization quando:

- Envolver operações de entrada e saída;
- Processamento de array ou objetos grandes;
- Cálculos matemáticos complexos;
- Criação de estruturas complexas;
- Operações maiores que alguns milissegundos.

## Atualização do Estado

Apesar de ser possível alterar o valor diretamente utilizando a função set, é desaconselhável uma vez que esta operação não é atômica, portanto, caso múltiplas atualizações sejam feitas concorrentemente poderá gerar [condição de corrida](obsidian://open?vault=anotacoes_ti&file=Programa%C3%A7%C3%A3o%2FMiscel%C3%A2nea%2FConceitos%2FCondi%C3%A7%C3%A3o%20de%20corrida). Podemos verificar no ilustrativo abaixo: 

```javascript
// ❌ ERRADO - pode não funcionar como esperado
setCount(count + 1);
setCount(count + 1);
setCount(count + 1);
// Resultado: +1 (não +3!)

// ✅ CORRETO
setCount(prev => prev + 1);
setCount(prev => prev + 1);
setCount(prev => prev + 1);
// Resultado: +3
```

## Trabalhando com Objetos:

Ao atualizar um objeto contido no useState, devemos sempre criar um novo objeto e nunca atualizar o existente:

```javascript
const [usuario, setUsuario] = useState({ nome: '', idade: 0 });

// ✅ CORRETO - cria novo objeto
setUsuario({ ...usuario, nome: 'João' });

// ❌ ERRADO - modifica o existente
usuario.nome = 'João';
```


## Pontos importantes:

### Atualizações são assincronas:

> A atualização do estado no react é feita em batching, ou seja, o react acumula múltiplas atualizações antes de re-renderizar o componente.

### React compara por referência:

> Tipos que não são primitivos, o react compara valores verificando se ambos apontam para o mesmo lugar na memória, e não se tem o mesmo conteúdo.

### Preserva o estado entre re-renderizações:

> O react mantém uma estrutura da dados separada para armazenar os estados de cada componente. Dessa forma, informações não são perdidas de uma renderização para a outra. O estado apenas é perdido quando o componente é desmontado ou quando a key de um componente muda.

## Quando usar:

- Para armazenar dados que mudam na interface
- Quando o valor altera a renderização do componente
- Precisar de dados temporários

## Quando não usar:

- Quando o valor não alterar a renderização (useRef)
- O calculo é derivado de outros estados (calcular diretamente)
- Precisar compartilhar com muitos componentes (Context ou Redux)






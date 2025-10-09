## Definição:

> É um hook que permite o uso de efeitos colaterais *(side effects)* em componentes funcionais, sendo esses efeitos operações que afetam pontos fora da função. Tais quais:

### Exemplos:

- Requisições HTTP *(fetch ou axios)*;
- Manipulação direta do DOM;
- Subscrições *(websockets ou eventos)*;
- Timers *(setTimeOut ou setInterval)*;
- Logs no console;
- Sincronização com APIs externas.

## Criação:

> Antigamente, apenas componentes de classe tinham acesso aos métodos de ciclo de vida *(como por exemplo componentDidMount, componentDidUpdate, componentWillUnmount)*. Dessa forma, o useEffect unifica essas três funções em apenas uma única API para componentes funcionais.

## Anatomia:

```javascript
useEffect(() => {
	...codigo...
}, [dependências]);
```

1. É passado uma arrow function que contenha o efeito *(função)* a qual deseja que execute;
2. Contém as dependências que, quando atualizadas, engatilharão o efeito ocorrer novamente.

**Obs:** Caso a área de dependências seja deixada vazia, o efeito ocorrerá novamente a cada re-renderização da pagina, o que pode causar problemas de performance!

## Usos:

### Limpeza:

O useEffect pode retornar uma função que será executada antes do próximo efeito ou quando o componente for desmontado.

### Exemplo:

```javascript
useEffect(() => {
  // Setup
  const timer = setInterval(() => {
    console.log('Tick');
  }, 1000);

  // Cleanup
  return () => {
    clearInterval(timer);
    console.log('Timer limpo!');
  };
}, []);
```

Nesse contexto, o return será executado antes do efeito executar novamente *(quando as dependências mudam)* ou quando o componente for desmontado. 

### Requisição HTTP:

```javascript
function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    setLoading(true);
    
    fetch(`/api/users/${userId}`)
      .then(res => res.json())
      .then(data => {
        setUser(data);
        setLoading(false);
      });
  }, [userId]); // Re-executa quando userId muda

  return loading ? <p>Carregando...</p> : <p>{user.name}</p>;
}
```

1. Assim que a página renderizar, setLoading será definido como true e o fetch dos dados do usuário será feito;
2. Ao final do useEffect, setLoading será tornado false;
3. Então, efeito será reaplicado toda a vez que o userId mudar.


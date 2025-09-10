# Memória Compartilhada

> Em uma arquitetura **[MIMD](obsidian://open?vault=Obsidian&file=anotacoes_ti%2FPrograma%C3%A7%C3%A3o%2FMiscel%C3%A2nea%2FConceitos%2FClassifica%C3%A7%C3%A3o%20de%20Flynn#^As-classificações-se-dividem-nas-quatro-categorias-abaixo) (Multiple Instruction, Multiple Data)**, o compartilhamento de memória é uma das formas fundamentais de organização para permitir que múltiplos processadores trabalhem em conjunto. Nestes sistemas, **cada UCP (Unidade Central de Processamento) pode executar instruções diferentes e utilizar dados diferentes**.

### Conceitos centrais:

Em arquiteturas com memória compartilhada são dividias em duas classes principais: [UMA](obsidian://open?vault=Obsidian&file=anotacoes_ti%2FPrograma%C3%A7%C3%A3o%2FComputa%C3%A7%C3%A3o%20de%20Nuvem%20e%20Alto%20Desempenho%2FGloss%C3%A1rio%2FUMA) e [NUMA](obsidian://open?vault=Obsidian&file=anotacoes_ti%2FPrograma%C3%A7%C3%A3o%2FComputa%C3%A7%C3%A3o%20de%20Nuvem%20e%20Alto%20Desempenho%2FGloss%C3%A1rio%2FNUMA). Neste modelo, **todos os processadores acessam um espaço de endereçamento global**. Os processadores podem operar de forma independente, mas compartilham a mesma memória, o que significa que as alterações feitas por um processador são visíveis para todos os outros.


![[Arquitetura_Memoria_Compartilhada.png]]
### Vantagens:

- Facilidade de utilização de variáveis compartilhadas;
- Tempo de acesso rápido a essas variáveis em comparação com a memória distribuída.

### Desvantagens:

- Aumento do tráfego na interconexão entre processadores e memória com o crescimento do número de processadores, o que pode levar à:
	- Instabilidade;
	- Necessidade de o programador ser responsável pela sincronização do acesso à memória compartilhada para evitar erros.


# Memória Distribuída

### Conceitos centrais:

Cada processador acessa somente sua memória local, e não existe o conceito de endereçamento global. As mudanças realizadas na memória local de um processador não afetam a memória dos outros processadores. A comunicação entre os processadores ocorre **através de uma rede de comunicação**, e o acesso à memória não local é realizado por meio de programação explícita, geralmente por troca de mensagens.

![[Arquitetura_Memoria_Distribuida.png]]
### Vantagens:

- Aumento proporcional da quantidade de memória com o número de processadores;
- Acesso independente de cada processador à sua memória, sem a necessidade de manter a coerência entre eles;
- Pode ser construído a partir de processadores e redes já existentes, como em clusters de computadores.

### Desvantagens:

- Programador é o responsável pelo compartilhamento de dados entre os processadores (exigindo o envio explícito de dados); 
- Mapeamento de estruturas de dados que dependem de endereçamento global é dificultado.


# Arquitetura Híbrida

### Conceitos centrais:

Combinar os componentes de ambas as arquiteturas para capitalizar suas vantagens e mitigar suas desvantagens.

### Vantagens aproveitadas:

- Em um sistema híbrido, os componentes que possuem memória compartilhada mantêm a **facilidade de utilização de variáveis compartilhadas** e o **tempo de acesso rápido** a essas variáveis dentro de seus próprios grupos de processadores. As tarefas dentro de um desses componentes compartilham um espaço de endereçamento global, que pode ser lido e escrito assincronamente, sem a necessidade de comunicação explícita para o compartilhamento de dados local;
- A abordagem híbrida permite que a quantidade total de memória aumente proporcionalmente à quantidade de processadores em todo o sistema, característica da memória distribuída. Cada grupo de processadores com memória compartilhada pode ser visto como um "nó" em uma arquitetura distribuída. Isso significa que esses grupos podem operar com alguma independência, e o sistema como um todo pode ser construído a partir de processadores e redes já existentes, como clusters de computadores.

### Desvantagens mitigadas:

- A memória puramente compartilhada sofre com o aumento do tráfego na interconexão entre processadores e memória à medida que o número de processadores cresce, levando à instabilidade e limitações de largura de banda. Na arquitetura híbrida, essa limitação é contornada ao organizar o sistema em múltiplos componentes (nós) com memória compartilhada. A comunicação entre esses nós ocorre de forma distribuída, reduzindo o gargalo de tráfego em uma única interconexão de memória compartilhada massiva;
- A memória distribuída exige que o programador seja responsável pelo compartilhamento explícito de dados entre os processadores, o que pode ser difícil para mapear estruturas de dados baseadas em endereçamento global e resulta em tempos de acesso não uniformes à memória não local. No modelo híbrido, essa complexidade é gerenciada: dentro de cada nó de memória compartilhada, os dados são acessados facilmente. Apenas a comunicação entre os nós exige programação explícita (troca de mensagens), mas essa comunicação é menos frequente e mais gerenciável do que tentar um compartilhamento global de dados em um sistema puramente distribuído com muitos processadores.
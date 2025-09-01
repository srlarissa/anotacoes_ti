
# Memória Compartilhada

Em uma arquitetura **[MIMD](obsidian://open?vault=Obsidian&file=anotacoes_ti%2FPrograma%C3%A7%C3%A3o%2FMiscel%C3%A2nea%2FConceitos%2FClassifica%C3%A7%C3%A3o%20de%20Flynn#^As-classificações-se-dividem-nas-quatro-categorias-abaixo) (Multiple Instruction, Multiple Data)**, o compartilhamento de memória é uma das formas fundamentais de organização para permitir que múltiplos processadores trabalhem em conjunto. Nestes sistemas, **cada UCP (Unidade Central de Processamento) pode executar instruções diferentes e utilizar dados diferentes**.

### Conceitos centrais:

Em arquiteturas com memória compartilhada são dividias em duas classes principais: [UMA](obsidian://open?vault=Obsidian&file=anotacoes_ti%2FPrograma%C3%A7%C3%A3o%2FComputa%C3%A7%C3%A3o%20de%20Nuvem%20e%20Alto%20Desempenho%2FGloss%C3%A1rio%2FUMA) e [NUMA](obsidian://open?vault=Obsidian&file=anotacoes_ti%2FPrograma%C3%A7%C3%A3o%2FComputa%C3%A7%C3%A3o%20de%20Nuvem%20e%20Alto%20Desempenho%2FGloss%C3%A1rio%2FNUMA), e **todos os processadores acessam um espaço de endereçamento global**. Isso significa que, independentemente de qual processador modificou um dado na memória, essa **mudança é visível para todos os outros processadores**. A comunicação entre os processadores é realizada indiretamente através de operações de leitura (loads) e escrita (stores) nesse espaço de endereçamento compartilhado.

### Vantagens

- **Facilidade de utilização de variáveis compartilhadas**: O programador não precisa implementar comunicação explícita para compartilhar dados, pois as variáveis são acessíveis a todas as tarefas;

- **Tempo de acesso rápido**: Comparado à memória distribuída, o tempo para acessar variáveis compartilhadas é geralmente mais rápido, especialmente para dados locais em sistemas NUMA;

### Desvantagens

- **Sincronização**: O programador é o responsável pela **sincronização do acesso à memória compartilhada** para evitar condições de corrida (race condition) e garantir a corretude dos dados. Se a sincronização não for adequada, resultados incorretos podem ser produzidos. Técnicas como locks e semáforos são usadas para proteger dados ou código compartilhados;

- **Escalabilidade limitada em [UMA](obsidian://open?vault=Obsidian&file=anotacoes_ti%2FPrograma%C3%A7%C3%A3o%2FComputa%C3%A7%C3%A3o%20de%20Nuvem%20e%20Alto%20Desempenho%2FGloss%C3%A1rio%2FUMA)**: O aumento no número de processadores pode levar a um aumento significativo do tráfego na interconexão entre processadores e memória, causando instabilidade e gargalos de largura de banda;

- **Complexidade de gerenciamento de cache**: Em sistemas multi-core e [NUMA](obsidian://open?vault=Obsidian&file=anotacoes_ti%2FPrograma%C3%A7%C3%A3o%2FComputa%C3%A7%C3%A3o%20de%20Nuvem%20e%20Alto%20Desempenho%2FGloss%C3%A1rio%2FNUMA), manter a coerência de cache entre os múltiplos processadores é um desafio complexo, embora seja geralmente tratado pelo hardware

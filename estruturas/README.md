# Algoritmos e Estruturas

Estruturas de dados foram criadas para quando queremos agrupar dados. Por exemplo, o nome e a idade de uma pessoa. E esse agrupamento pode conter outros agrupamentos dentro, como uma estante que tenha um gaveteiro: o gaveteiro é um agrupamento de gavetas, mas ele está na estante, que também tem prateleiras e talvez outros gaveteiros.

Quando uma estrutura é um agrupamento de vários itens do mesmo tipo, ela é uma coleção. No exemplo, o gaveteiro é uma coleção de gavetas.


## Vetor (array)

O gaveteiro poderia ser representado pelo vetor: o gaveteiro seria um vetor, e cada gaveta seria uma variável dentro do vetor, um espaço disponível para guardar o que se deseja.


## Lista ligada (Linked List)

Quando vamos passar por algum procedimento burocrático, falamos com um departamento, ele nos envia a um segundo departamento, que nos envia a um terceiro... E assim por diante. Nem sabemos quando haverá um fim, até que cheguemos ao último departamento.

As listas ligadas funcionam da mesma forma. Um elemento aponta para o seguinte, o seguinte aponta para outro, assim por diante.


## Vetor x Lista Ligada

Mas se eu já posso guardar as coisas em vetores, porque foram inventadas as listas ligadas?

Quando criamos um vetor no computador, ele vai colocar nossa coleção de itens em um lugar na memória. Ele precisa saber o tamanho exato que precisa reservar. Como quando você quer comprar um gaveteiro, você precisa de antemão saber quantas gavetas vai precisar.

No caso da lista, o computador reserva os espaços em memória conforme os itens forem sendo colocados na lista ligada. No processo burocrático, você reserva um dia para ir a um departamento. Chegando lá, te direcionam a um segundo departamento. Então você precisa reservar mais um horário para esse segundo departamento, onde você não sabia previamente que teria que ir. Para cada lugar que for, você precisará reservar um novo horário.


## Tabela hash

A tabela hash funciona como um arquivo físico. Se você pega um registro de 27-03-1986, você vai guardar o registro na gaveta onde tem a etiqueta de 1986. Você pode ter gavetas vazias e gavetas com muitos registros, mas será mais fácil encontrar por ter separado por anos.

Uma equivalência do arquivo físico para a tabela hash seria: as etiquetas representam as chaves da tabela hash, e os registros que estão na gaveta daquela etiqueta são o valor daquela chave. A chave e o valor juntos formam um par.

Curiosidade: existem linguagens da programação onde a tabela hash é chamada de dicionário ou hashmap.


## Fila

Fila em programação tem a mesma utilidade de uma fila no mundo real. Pensemos na fila do caixa do supermercado. Quando uma pessoa nova chega, ela se posiciona atrás da última pessoa que chegou antes dela. Quando quem está atendendo chama a próxima pessoa, quem deve ser atendido é a primeira pessoa da fila, pois é a pessoa que está esperando há mais tempo.


## Pilha

Pilhas também foram nomeadas de acordo com uma coisa que conhecemos do cotidiano. Você acabou de comer e colocou seu prato em cima da pia. Em seguida, uma outra pessoa terminou e colocou o prato dela em cima do seu prato. Qual o primeiro prato que você irá pegar da PILHA de pratos para lavar? O último que foi colocado na pilha. E em seguida? O que foi colocado antes dele.

Lembra da expressão "os últimos serão os primeiros"? Pois é, é assim que pilhas funcionam.


## Implementações

### Lista ligada - implementação

- Nó
- Ponteiro para próximo nó
- Inserir
- Procurar
- Excluir
- Atualizar


### Tabela hash (hash table / hash map)

- Par
  - Chave
  - Valor
- Inserir
- Procurar
- Excluir
- Atualizar


### Fila (Queue)

- Itens
- Início
- Fim
- Inserir
- Pegar


### Pilha (Stack)

- Itens
- Início
- Fim
- Topo
- Inserir
- Pegar


### Árvore de busca binária (binary search tree)

- Nó
  - Representação humana / convenção
  - Filho esquerda
  - Filho direita
- Inserir
- Procurar
- Excluir
- Atualizar


#### Árvore de busca binária - BALANCEADA (Binary search tree - balanced)

- Inserir
- Excluir


#### Binary heap

- Prioridades
- Inserir
- Procurar
- Excluir
- Atualizar
- Min / Max Heap


### Ordenação de vetor

- Quicksort
- Heapsort


# Micro-services

Divisão de um serviço em módulos, para rodar separado


# Big O

- mede o "tempo" de um algoritmo
- revisar algoritmos planilha

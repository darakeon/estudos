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


## Árvore

A estrutura chamada de Árvore é baseada nas árvores do mundo real. As árvores que conhecemos têm um tronco e dele saem galhos. Destes galhos saem outros galhos. E assim por diante, até chegar às folhas.

A estrutura é representada como uma árvore, mas de ponta cabeça, por causa da forma como escrevemos - de cima para baixo. Por exemplo:

```
                 A
              __/|\__
           __/   |   \__
        __/      |      \__
       B         C         D
     _/|\_     _/|\_     _/|\_
    E  F  G   H  I  J   K  L  M
```

Cada galho pode ter diversos galhos crescendo dele na árvore do mundo real, assim é também na estrutura de Árvore. O ponto onde um galho termina (por exemplo, a letra `D` na Árvore acima) é chamado de Nó. O início da árvore, onde tem um `A`, também é chamado de Nó, mas é um Nó especial, o Nó Raiz.

A árvore inicia com o Nó `A`. Então se ramifica para 3 galhos. Os 3 galhos saindo de `A` também têm seus Nós: o galho da sua esquerda tem o Nó `B`, o galho do meio tem o Nó `C` e o galho da sua direita tem o Nó `D`.

Para falar das ligações da estrutura de árvore, dizemos que:

- `B`, `C` e `D` são Filhos de `A`;

- `A` é o Pai de `B`, `C` e `D`;

- `E`, `F` e `G` são Filhos de `B`;

- `B` é o Pai de `E`, `F` e `G`;

- e assim por diante.

Um Nó que não tem nenhum filho é chamado de Folha - pois das folhas não saem novos galhos. No exemplo, nossos Nós Folha são: `E`, `F`, `G`, `H`, `I`, `J`, `K`, `L` e `M`.


## Árvore binária

Uma árvore binária é uma árvore em que cada nó pode ter, no máximo, `2` filhos. Ela segue todas as regras mencionadas na árvore.

```
              A
           __/ \__
        __/       \__
       B             D
     _/ \_         _/ \_
    E     G       K     M
```


## Busca binária

Busca binária é um tipo de busca usado para otimizar tempo. Por exemplo, pense em uma lista de notas organizada por matrícula. Você sabe seu número de matrícula, mas a lista é enorme.

Foi descoberto um jeito mais simples de fazer isso. Você vai até a metade da lista. Se o número da matrícula na metade da lista for menor que o seu significa que você está depois daquela matrícula. Isso faz com que você possa ignorar a metade de cima da lista e olhar apenas na metade de baixo.

Você pega então a parte de baixo da lista. Ainda tem muita coisa. Você segue o mesmo método: divide a nova lista em duas novamente e olha se o número do meio é menor ou maior que sua matrícula. Dessa vez, você descobre que a matrícula do meio é maior que a sua. Então sua matrícula só pode estar antes dela. A parte abaixo dela pode ser ignorada.

Dessa forma, primeiro você descarta metade da lista, depois metade da metade (um quarto), e assim por diante, até sobrar apenas a sua matrícula. Isso é uma busca binária.


## Árvore de busca binária

Essa árvore é uma combinação da árvore binária com a busca binária.

Além das regras de árvore e da regra de árvore binária, temos regras para adicionar elementos:

- Se for o primeiro, é colocado no Nó Raiz;
- Se não, comparamos com o primeiro:
  - Se for menor que o primeiro, olhamos para a esquerda;
  - Se for maior que o primeiro, olhamos para a direita.

Exemplo: adicionar `4`, `2`, `6`:

- adicionar `4`:

```
              4
```

- adicionar `2`:

```
              4
           __/
        __/
       2
```

- adicionar `6`:

```
              4
           __/ \__
        __/       \__
       2             6
```

Para seguir adicionando elementos, continuamos seguindo as mesmas regras. Ex:

- adicionar `3`:
  - é menor que `4`: vou para a esquerda do `4`;
  - é maior que `2`: vou para a direita do `2`;
  - está vazio, coloco o `3` ali.

```
              4
           __/ \__
        __/       \__
       2             6
        \_
          3
```

- adicionar `5`:
  - é maior que `4`, vou para a direita do `4`;
  - é menor que `6`, vou para a esquerda do `6`;
  - está vazio, coloco o `5` ali.

```
              4
           __/ \__
        __/       \__
       2             6
        \_         _/
          3       5
```

- adicionar `7`:
  - é maior que `4`, vou para a direita do `4`;
  - é maior que `6`, vou para a direita do `6`;
  - está vazio, coloco o `7` ali.

```
              4
           __/ \__
        __/       \__
       2             6
        \_         _/ \_
          3       5     7
```

- adicionar `1`:
  - é menor que `4`, vou para a esquerda do `4`;
  - é menor que `2`, vou para a esquerda do `2`;
  - está vazio, coloco o `7` ali.

```
              4
           __/ \__
        __/       \__
       2             6
     _/ \_         _/ \_
    1     3       5     7
```


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

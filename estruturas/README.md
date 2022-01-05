# Algoritmos e Estruturas

Estruturas de dados foram criadas para quando queremos agrupar dados. Por exemplo, o nome e a idade de uma pessoa. E esse agrupamento pode conter outros agrupamentos dentro, como uma estante que tenha um gaveteiro: o gaveteiro é um agrupamento de gavetas, mas ele está na estante, que também tem prateleiras e talvez outros gaveteiros.

Quando uma estrutura é um agrupamento de vários itens do mesmo tipo, ela é uma coleção. No exemplo, o gaveteiro é uma coleção de gavetas.


## Vetor (array)

O gaveteiro poderia ser representado pelo vetor: o gaveteiro seria um vetor, e cada gaveta seria uma variável dentro do vetor, um espaço disponível para guardar o que se deseja.


### Facilidade de implementação

Vetores vêm já prontos por padrão nas linguagens de programação. Por esse motivo, você não cria uma implementação sua de vetor.


### Exemplo de uso

Pensemos no desenvolvimento de um jogo. Abaixo está o mapa do caminho que precisa ser percorrido para chegar ao castelo, sendo que cada <> é uma cidade:

```
                                 P
                                /\
                                ||
                              M_||_M
          <>                  | __ |
         /  \            <>---| || |
 <>---<>´    \         _/
              `<>---<>´
```

A cada fase você pode ganhar 3 estrelas, cada uma dependendo de algo que fez na cidade. Esse seria um bom exemplo de onde pode ser usado vetor em um projeto: você teria um vetor com 3 posições, uma para cada estrela, para dizer se a pessoa ganhou ou não a estrela em uma cidade.

E cada cidade poderia ser representada com suas estrelas:

```
                                                 P
                                                /\
                                                ||
                                              M_||_M
               <** >                          | __ |
               /   \                  <   >---| || |
 <***>---<***>´     \               _/
                     `<  *>---<* *>´
```


## Lista ligada (Linked List)

Quando vamos passar por algum procedimento burocrático, falamos com um departamento, ele nos envia a um segundo departamento, que nos envia a um terceiro... E assim por diante. Nem sabemos quando haverá um fim, até que cheguemos ao último departamento.

As listas ligadas funcionam da mesma forma. Um elemento aponta para o seguinte, o seguinte aponta para outro, assim por diante.


### Facilidade de implementação: simples

A implementação de uma lista ligada conta com dois componentes: um para representar a lista em si e outro para representar o item.

O que pode confundir na hora de criar o item é o fato de que ele precisa apontar o próximo item. Para isso é usado ponteiro: o item atual "sabe" onde na memória do computador o próximo item deve ser encontrado.

Um ponto de atenção na implementação da lista em si é a exclusão de itens. Dada uma lista:

```
  A -> B -> C -> D -> E
```

Temos `A` como primeiro item, ele está apontando para `B`, e `B` está apontado para `C`. Caso eu exclua o item `B`:

```
  A -> ???  C -> D -> E
```

Temos agora `A` apontando para o vazio e `C`, `D` e `E` perdidos no limbo. Precisamos ter o cuidado de fazer `A` apontar para o `C`.

```
  A -> C -> D -> E
```

Assim não perdemos um pedaço da lista.


### Exemplo de uso

A lista ligada serve para substituir o vetor em casos onde não se sabe a quantidade de itens quando vamos criar a coleção. Um bom exemplo é um sistema de vendas online. Quando a pessoa começa a comprar, você ainda não sabe qual a quantidade de itens que a pessoa vai comprar.

Primeiro, pense que a pessoa adicionou um chocolate:

```
  chocolate
```

Depois, quis comprar um pão:

```
  chocolate -> pão
```

Aí decidiu comprar queijo:

```
  chocolate -> pão -> queijo
```

Então resolveu que não queria mais o pão, ia comer só queijo mesmo:

```
  chocolate -> queijo
```

Os itens apontarem uns para os outros não quer dizer que eles tenham alguma ligação, isso é feito apenas para que a lista possa crescer indefinidamente, pois cada item "sabe" onde encontrar o próximo item. Para quem usa o sistema, essa ligação é invisível.


## Vetor x Lista Ligada

Mas se eu já posso guardar as coisas em vetores, porque foram inventadas as listas ligadas?

Quando criamos um vetor no computador, ele vai colocar nossa coleção de itens em um lugar na memória. Ele precisa saber o tamanho exato que precisa reservar. Como quando você quer comprar um gaveteiro, você precisa de antemão saber quantas gavetas vai precisar.

No caso da lista, o computador reserva os espaços em memória conforme os itens forem sendo colocados na lista ligada. No processo burocrático, você reserva um dia para ir a um departamento. Chegando lá, te direcionam a um segundo departamento. Então você precisa reservar mais um horário para esse segundo departamento, onde você não sabia previamente que teria que ir. Para cada lugar que for, você precisará reservar um novo horário.


## Tabela hash

A tabela hash funciona como um arquivo físico. Se você pega um registro de 27-03-1986, você vai guardar o registro na gaveta onde tem a etiqueta de 1986. Você pode ter gavetas vazias e gavetas com muitos registros, mas será mais fácil encontrar por ter separado por anos.

Uma equivalência do arquivo físico para a tabela hash seria: as etiquetas representam as chaves da tabela hash, e os registros que estão na gaveta daquela etiqueta são o valor daquela chave. A chave e o valor juntos formam um par.

Curiosidade: existem linguagens da programação onde a tabela hash é chamada de dicionário ou hashmap.


### Facilidade de implementação: simples

Na tabela hash, cada item armazenado tem uma chave. Essa chave é transformada em um número através de uma conta. Esse número diz qual a posição em que o item deve ficar. Esses itens são guardados em vetores. Quando um item é buscado usando sua chave, a conta só precisa ser refeita para saber onde está o item.


### Exemplo de uso

Pense em um aplicativo em que você coloca uma palavra e ele te traz os significados. A palavra "dicionário" deve ter vindo a sua mente. O motivo de algumas linguagens usarem "dicionário" ao invés de hash table / hash map é a semelhança da ideia da Tabela Hash com os dicionários: você busca por uma palavra e vai a posição correta para encontrar os significados. No caso do dicionário físico a posição é apenas "calculada" pela ordem alfabética. Um mini dicionário ficaria assim:

```
chocolate: produto alimentício de cor marrom, sólido, pastoso ou em pó, que tem como matéria-prima o cacau a que se adicionam açúcar e certas substâncias aromáticas.

queijo: produto obtido pela fermentação da coalhada, submetida à compressão e posta a secar no cincho.
```

Onde `chocolate` e `queijo` são chaves, e os significados deles são os valores das chaves.


## Fila

Fila em programação tem a mesma utilidade de uma fila no mundo real. Pensemos na fila do caixa do supermercado. Quando uma pessoa nova chega, ela se posiciona atrás da última pessoa que chegou antes dela. Quando quem está atendendo chama a próxima pessoa, quem deve ser atendido é a primeira pessoa da fila, pois é a pessoa que está esperando há mais tempo.


### Facilidade de implementação: média

Filas podem ser implementadas tanto usando vetores quanto usando listas para guardar seus itens. A implementação mais simples é feita com listas. Com um vetor, cada vez que pegamos o primeiro elemento da fila, precisaríamos fazer os outros elementos "darem um passo a frente", veja:

```
| A | B | C | D | E | F | G | H | I | J | K |
```

Se pegamos o primeiro item, `A`:

```
|   | B | C | D | E | F | G | H | I | J | K |
```

Precisamos mover os outros todos, para que possamos depois pegar o `B`, assim por diante:

```
| B | C | D | E | F | G | H | I | J | K |   |
```

No caso de uma lista ligada, podemos apenas apontar o início da lista para o próximo elemento.

```
.- início           .- fim
|                   |
A -> B -> C -> D -> E
```

Pego `A`:

```
.- início           .- fim
|                   |
     B -> C -> D -> E
```

Aponto para o elemento seguinte:

```
     .- início      .- fim
     |              |
     B -> C -> D -> E
```

É necessário guardar algumas informações para se ter uma fila:
- Uma coleção para guardar os elementos;
- A informação de onde está o primeiro elemento da fila, para poder pegar ele quando for para pegar um elemento da lista;
- A informação de onde está o último elemento da fila, para poder colocar o próximo elemento depois dele.


### Exemplo de uso

O sistema da impressora implementa uma fila. Quando a impressora recebe diversos documentos, o primeiro que ela vai imprimir é o primeiro que chegou para ela. Em seguida ela imprime o que chegou depois. Até terminar a fila de impressão.


## Pilha

Pilhas também foram nomeadas de acordo com uma coisa que conhecemos do cotidiano. Você acabou de comer e colocou seu prato em cima da pia. Em seguida, uma outra pessoa terminou e colocou o prato dela em cima do seu prato. Qual o primeiro prato que você irá pegar da PILHA de pratos para lavar? O último que foi colocado na pilha. E em seguida? O que foi colocado antes dele.

Lembra da expressão "os últimos serão os primeiros"? Pois é, é assim que pilhas funcionam.


### Facilidade de implementação: média

A pilha é implementada usando um vetor ou uma lista para guardar seus elementos.

Usando vetor, quando adiciono um elemento, coloco no final do vetor.

Minha pilha:

```
| A | B | C |   |   |   |   |
```

Adiciono `D`:

```
| A | B | C | D |   |   |   |
```

Como o último elemento que coloquei será o primeiro que vou pegar (como em uma pilha de pratos), minha pilha apenas volta ao estado anterior removendo `D`, e não preciso andar com os elementos como na fila.

```
| A | B | C | D |   |   |   |
```

se torna:

```
| A | B | C |   |   |   |   |
```

A vantagem de usar uma lista na pilha é por a lista não precisar ter um tamanho fixo.

É necessário guardar algumas informações para se ter uma pilha:
- Uma coleção para guardar os elementos;
- A informação de onde está o último elemento inserido, que será o primeiro a ser retirado e também será depois dele que qualquer elemento novo será adicionado;

Na pilha, inserimos e removemos do mesmo lado: o topo da pilha.


### Exemplo de uso

Caso você for criar um browser, você usará uma pilha para implementar o histórico de páginas. Suponha que eu acesso a página do Google. Então faço uma pesquisa sobre chocolate. E entro na página de um mercado. O que acontece quando clico no botão de voltar?

Acessei o google (adiciono Google na pilha):

```
Google
```

Pesquisei chocolate (adiciono Pesquisa na pilha):

```
Pesquisa Chocolate
Google
```

Abri a página do mercado (adiciono Mercado na pilha):

```
Página do Mercado
Pesquisa Chocolate
Google
```

Cliquei no botão de voltar (tiro Mercado na pilha):

```
Pesquisa Chocolate
Google
```

Eu volto a ver a página de Pesquisa de Chocolate. Repare que o topo da minha pilha representada aqui é sempre a página que estou vendo, mas as outras páginas que vi antes não somem da minha pilha. O único momento em que isso acontece é quando clico para voltar no browser.


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

Essa estrutura não linear é usada para facilitar a busca. Se eu quiser chegar até o `M`, eu só precisaria passar pelo `A` e pelo `D`, não por todos os elementos que existem, como seria em uma estrutura linear. Mais a frente veremos como se faz isso.


### Facilidade de implementação: simples

Uma árvore se parece com uma lista ligada em sua implementação. A diferença é que, ao invés de ligar um elemento a apenas um outro elemento, que vem depois, você pode ligar o elemento a vários outros elementos, seus filhos.

Uma árvore deve apenas saber quem é seu primeiro Nó, o Nó Raiz. Esse Nó deve ter uma coleção de elementos para seus filhos. Se não houver filhos, a coleção está vazia.


### Exemplo de uso

Se você fizer um site tenha um formulário de cadastro de endereços, você poderia usar uma árvore para guardar estados e cidades. Sabemos que um estado tem diversas cidades e um país tem diversos estados.

Exemplo:

```
           _____ Brasil _____
          /                  \
     Amazonas              Tocantins
    /        \            /         \
Humaitá    Manacapuru  Paranã     Sampaio
```


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


### Facilidade de implementação: simples

A diferença de implementação para a árvore é que, ao invés de haver uma coleção de filhos, o Nó desta árvore terá apenas dois: o filho da direita e o filho da esquerda.


### Exemplo de uso

Se fôssemos criar um jogo onde, dependendo da escolha da pessoa, a estória toma um rumo diferente, e as escolhas fossem de "Sim" ou "Não", poderíamos armazenar a estrutura da história em uma árvore binária: caso a pessoa respondesse sim, iria para a esquerda. Caso não, iria para a direita.


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
  - Se for maior ou igual ao primeiro, olhamos para a direita.

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


### Facilidade de implementação: simples

A única adição de regra feita na árvore de busca binária em relação a árvore binária é a exigência de uma ordenação: um elemento menor que o elemento do nó deve ser encaminhado para a esquerda, enquanto um maior ou igual deve ser encaminhado para a direita.


### Exemplo de uso

Essas árvores são usadas para ordenar coleções de elementos. Exemplo:

```
              4
           __/ \__
        __/       \__
       2             6
     _/ \_         _/ \_
    1     3       5     7
```

Se esses números tivessem sido colocados em uma lista, talvez estivessem desordenados. Caso tivessem sido colocados ordenados, ainda seria uma lista {`1`,`2`,`3`,`4`,`5`,`6`,`7`}, e para chegar ao 7 eu precisaria passar pelos 6 elementos anteriores.

No caso da árvore de busca binária, eu olho para o primeiro elemento, sei que `7` é maior que `4`. Vou para a direita. `7` também é maior que `6`. Para a direita novamente. Encontro o `7`. Tendo passado por apenas dois elementos.


## Árvore de busca binária balanceada (AVL)

Um problema é que, dependendo da ordem que os elementos entrarem, a árvore pode ficar com muito mais coisa de um lado que de outro.

Por exemplo, se adicionarmos na ordem { `2`, `3`, `1`, `5`, `4`, `6`, `7` }, a árvore ficaria assim:

```
              2
           __/ \__
        __/       \__
       1             3
                      \_
                        5
                      _/ \_
                     4     6
                            \_
                              7
```

A árvore do item anterior estava muito mais fácil de chegar ao `7`.

Para corrigir isso existem as árvores binárias balanceadas. A regra é que nenhum Nó tenha mais de 1 nível de diferença entre o filho da esquerda e o filho da direita. Por exemplo, essa árvore já desobedece a regra:

```
0             2
           __/ \__
        __/       \__
1      1             3
                      \_
2                       5
                         \_
3                          6
```

Do lado esquerdo de `3` não temos nenhum filho, porém do lado direito temos DOIS níveis de filhos. A verificação deve ser feita para todos os nós.

Existem quatro formas de a árvore ficar desbalanceada.


### Tudo para a esquerda

Inserção: {`3`, `2`, `1`}

```
0             3
           __/
        __/
1      2
     _/
2   1
```

Usaremos uma `rotação a direita simples`. Consiste em inverter a relação do `2` e do `3` (`2` se torna pai de `3`), mantendo todo o resto da árvore sendo filho de quem era originalmente (`1` continua sendo filho de `2`).

```
-


0      2
     _/ \_
1   1     3
```


### Um para esquerda, um para direita

Inserção: {`3`, `1`, `2`}

```
0             3
           __/
        __/
1      1
        \_
2         2
```

Usaremos uma `rotação a direita dupla`. Antes de invertermos o `3` com seu filho da esquerda `1`, vamos inverter seu filho da esquerda `1` com o "neto" do `3`, que é o `2`, mantendo sempre a regra da árvore: `descendentes menores vão para a esquerda, descendentes maiores vão para a direita`:

```
0             3
           __/
        __/
1      2
     _/
2   1
```

Agora podemos usar a `rotação simples a direita`, invertendo o `3` com seu filho `2`.

```
-


0      2
     _/ \_
1   1     3
```


### Tudo para a direita

Inserção: {`1`, `2`, `3`}

```
0             1
               \__
                  \__
1                    2
                      \_
2                       3
```

Usaremos uma `rotação a esquerda simples`. Ela de fato é como a `rotação a direita simples`, mas gira a árvore para o lado contrário. Consiste em inverter a relação do `2` e do `1` (`2` se torna pai de `1`), mantendo todo o resto da árvore sendo filho de quem era originalmente.

```
-


0                    2
                   _/ \_
1                 1     3
```


### Um para direita, um para esquerda

Inserção: {`1`, `3`, `2`}

```
0             1
               \__
                  \__
1                    3
                   _/
2                 2
```

Usaremos uma `rotação a esquerda dupla` (espelho da `rotação a direita dupla`). Antes de invertermos o `1` com seu filho da direita `3`, vamos inverter seu filho da direita `3` com o "neto" do `1`, que é o `2`, mantendo sempre a regra da árvore: `descendentes menores vão para a esquerda, descendentes maiores vão para a direita`:

```
0             1
               \__
                  \_
1                   2
                     \_
2                      3
```

Agora podemos usar a `rotação simples a esquerda`, invertendo o `1` com seu filho `2`.

```
0


1                   2
                  _/ \_
2                1     3
```


### Quatro métodos?! Como decorar???

Se você tiver uma linha reta com os elementos desbalanceados, você usa `rotação simples`. Se não, você usa a `rotação dupla`.


### Exemplo inserindo vários Nós

Para manter a árvore balanceada, precisamos verificar se a regra está sendo obedecida toda vez que inserimos um novo elemento.

Exemplo:

- adicionar `2` (não desbalanceia):

```
0              2
```

- adicionar `3` (não desbalanceia):

```
0              2
                \__
                   \__
1                     3
```

- adicionar `1` (não desbalanceia):

```
0              2
            __/ \__
         __/       \__
1       1             3
```

- adicionar `5` (não desbalanceia):

```
0              2
            __/ \__
         __/       \__
1       1             3
                       \_
2                        5
```

- adicionar `4` (DESBALANCEIA!!!):

```
0              2
            __/ \__
         __/       \__
1       1             3
                       \_
2                        5
                        /
3                      4
```

Nesse caso, o desbalanceamento está acontecendo abaixo do `3`. O `5` está a `direita` do `3`, mas o `4` está a `esquerda` do `5`. Usaremos a `rotação dupla a esquerda`.

Primeiro, invertemos a relação do `5` com o `4`:

```
0              2
            __/ \__
         __/       \__
1       1             3
                       \_
2                        4
                          \
3                          5
```

Note que `4` passa a ser o filho de `3`.

Então invertemos o `3` e o `4`. Lembrando que o `5` continua sendo filho do `4`:

```
0              2
            __/ \__
         __/       \__
1       1             4
                    _/ \_
2                  3     5
```

- adicionar `7` (DESBALANCEIA!!!):

```
0              2
            __/ \__
         __/       \__
1       1             4
                    _/ \_
2                  3     5
                          \
3                          7
```

Agora, se olharmos, a árvore voltou a ser desbalanceada. Dessa vez, para o Nó `2`: do lado esquerdo temos apenas um nível, enquanto do lado direito temos três.

O maior nó filho de `2` é o `4`. O Nó que causou o desbalanceamento é o `7`. Se olharmos, `4` está a `direita` de `2` e `7` está a `direita` de `4`. Para resolver esse caso, usaremos `rotação simples a esquerda`: `4` passa a ser pai de `2`. `4` já era pai de `3` e de `5`

```
-


0                     4
                    _/|\_
1                  2  3  5
                  /       \
2                1         7
```

Pera, mas isso deixou de ser uma árvore binária! O que aquele `3` tá fazendo ali?!

Para esse caso, onde `4` já tinha na verdade um filho a esquerda, esse filho passa a ser seu "neto", descendo mais na árvore. Ou seja, `3` passa a ser filho do `2`.

```
-


0                     4
                    _/ \_
1                  2     5
                  / \     \
2                1   3     7
```

- adicionar `6` (DESBALANCEIA!!!):

```
-


0                     4
                    _/ \_
1                  2     5
                  / \     \
2                1   3     7
                          /
3                        6
```

Agora temos um desbalanceamento do Nó `5`: a esquerda nenhum filho, mas a direita temos dois níveis. `7` está a direita de `5`, mas `6` está a esquerda de `7`. Isso é mais um caso para a `rotação a esquerda dupla`!

Primeiro invertemos a relação de `7` com `6`:

```
-


0                     4
                    _/ \_
1                  2     5
                  / \     \
2                1   3     6
                            \
3                            7
```

Depois invertemos a relação de `5` com `6`, mantendo o `7` como filho do `6`:

```
-


0                     4
                    _/ \_
1                  2     6
                  / \   / \
2                1   3 5   7

-
```

Agora o `7` está mais perto de ser encontrado. Se a árvore incluísse `8`, `9` e `10` em seguida, SEM o balanceamento ficaria:

```
0             2
           __/ \__
        __/       \__
1      1             3
                      \_
2                       5
                      _/ \_
3                    4     6
                            \_
4                             7
                               \_
5                                8
                                  \_
6                                   9
                                     \_
7                                      10
```

Já usando a árvore balanceada:

```
0              4
            __/ \__
         __/       \__
1       2             8
      _/ \_         _/ \_
2    1     3       6     9
                  / \     \
3                5   7     10
```

Note que só preciso descer TRÊS níveis para encontrar o `10`. Já na árvore não balanceada, preciso descer SETE níveis para encontrar o `10`, mais que o dobro do trabalho.

Imagine se tivermos centenas, milhares de números, o quanto essa complexidade vai crescer! Por isso se usa a árvore balanceada: o trabalho na hora de balancear acaba poupando trabalho na hora de procurar.


## Fila de prioridade (Heap)

Existem dois tipos de fila de prioridade: aquelas em que o número menor é mais prioritário (MIN-HEAP) e aquelas em que o número maior é o mais prioritário (MAX-HEAP).

Como árvores são melhores para buscar e inserir elementos do que estruturas lineares, a fila de prioridades usa, de fato, uma árvore.

```
0              1
            __/ \__
         __/       \__
1       2             3
      _/ \_         _/ \_
2    4     5       6     7
    / \   / \     / \   / \
3  8   9 10  11  12 13 14 15
```

A fila de prioridade é um tipo de árvore binária, mas não é uma árvore de BUSCA binária. Isso porque sua meta é encontrar o valor mais prioritário: se ele estiver no topo da árvore, podemos sempre pegar o item do topo.

Por não ser uma árvore de busca binária, a inserção funciona de forma diferente.

Vamos usar um exemplo com o número `menor` sendo o MAIS prioritário.

Colocamos sempre o número na primeira posição "vaga" da árvore.

- insere `4`:

```
0              4
```

Depois que inserimos, precisamos verificar se o elemento está acima de todos os que são menos prioritários que ele. Nesse caso, só temos um elemento, portanto não precisamos fazer nada.

- insere `2`:

```
0              4
            __/
         __/
1       2
```

Dessa vez o `2` seria mais prioritário, mas está abaixo do `4`. Para arrumar isso, vamos inverter os dois.

```
0              2
            __/
         __/
1       4
```

- insere `3`:

```
0              2
            __/ \__
         __/       \__
1       4             3
```

O `3` não é mais prioritário que o `2`, então podemos seguir.

- insere `1`:

```
0              2
            __/ \__
         __/       \__
1       4             3
      _/
2    1
```

O `1` é mais prioritário que o `4`. Vamos inverter.

```
0              2
            __/ \__
         __/       \__
1       1             3
      _/
2    4
```

Mas ainda temos um problema. O `1` também é mais prioritário que o `2`. Para arrumar de fato a árvore, checamos o elemento inserido verificando todos aqueles que estão acima dele na árvore. Vamos inverter o `1` com o `2`.

```
0              1
            __/ \__
         __/       \__
1       2             3
      _/
2    4
```

E vamos inserindo e arrumando, sucessivamente.

Mas e quando tirarmos o elemento mais prioritário?

```
0              ?
            __/ \__
         __/       \__
1       2             3
      _/
2    4
```

Nesse caso, alguém vai precisar subir e assumir o lugar. Se subirmos o `3`, a árvore passa a estar errada, porque `2` é mais prioritário que `3`:

```
0              3
            __/
         __/
1       2
      _/
2    4
```

Então faz sentido sempre subir o filho mais prioritário, nesse caso, o `2`.

```
0              2
            __/ \__
         __/       \__
1       ?             3
      _/
2    4
```

Agora está vago o lugar em que o `2` estava antes. Portanto olhamos para os filhos do `2` e pegamos o mais prioritário para colocar no lugar dele. Nesse caso, seria o `4`, inclusive porque é seu único filho.

```
0              2
            __/ \__
         __/       \__
1       4             3
```

Então nossa árvore voltou a ser uma fila de prioridades, onde posso pegar o elemento do topo tendo certeza de ser o mais prioritário e não existem buracos vazios na árvore.


## Ordenação de Vetor


### Quicksort

A ideia do quicksort é pegar um elemento de um vetor desordenado e colocar todos os elementos maiores que ele depois dele, e todos os elementos menores antes dele. Existe mais de uma forma de escolher o elemento para usar:

- pegar sempre o primeiro elemento;
- pegar sempre o último elemento;
- pegar sempre o elemento do meio;
- pegar um elemento aleatório.

Para o exemplo, vamos pegar sempre o último elemento:

```
{1,9,4,8,3,5,7}
```

Último elemento: `7`

```
{1,4,3,5}  7  {9,8}
```

Agora sabemos que 7 está na posição certa. Então vamos repetir o procedimento para os dois pedaços novos que criamos, separando e posicionando o último elemento do conjunto. Vamos representar elementos abaixo para ficar mais claro a subdivisão em grupos acontecendo.

```
                7
           ____/ \____
  {1,4,3,5}           {9,8}
```

```
                7
           ____/ \____
          5           8
       __/ \__     __/ \__
{1,4,3}       {} {}       {9}
```

```
                7
           ____/ \____
          5           8
       __/ \__     __/ \__
      3                   9
     / \
   {1} {4}
```

```
                7
           ____/ \____
          5           8
       __/ \__     __/ \__
      3                   9
     / \
    1   4
```

Depois podemos colocar na mesma linha:

```
                7
           ____/ \____
          5           8
       __/ \__     __/ \__
    1_3_4                 9
```

```
                7
           ____/ \____
    1_3_4_5           8___9
```

```
    1_3_4_5_____7_____8___9
```

Assim temos o array ordenado.


### Heap sort

O Heap sort trata-se de usar uma fila de prioridades para ordernar uma coleção de elementos. Ao ler os elementos de uma Heap, leremos eles em ordem, devido a forma como é montada.

A primeira coisa a fazer é colocar todos os elementos na Heap, na ordem em que estão na coleção, de cima para baixo, da esquerda para a direita.

Digamos que nossa coleção de números seja:
{`5`,`4`,`1`,`7`,`3`,`2`,`6`}

```
0              5
            __/ \__
         __/       \__
1       4             1
      _/ \_         _/ \_
2    7     3       2     6
```

Após isso vamos a parte mais baixa a direita da árvore.

Temos os elementos `2` e `6`.

- Qual deles é mais prioritário?
  - `2`
- Ele é mais prioritário que o pai?
  - Não

Seguimos para o par do lado de `2` e `6`: `7` e `3`.

- Qual deles é mais prioritário?
  - `3`
- Ele é mais prioritário que o pai?
  - Sim!

Trocamos o `3` com o pai dele `4`.

```
0              5
            __/ \__
         __/       \__
1       3             1
      _/ \_         _/ \_
2    7     4       2     6
```

Como não existem mais Nós na última linha, subimos para a penúltima. Nosso par dessa vez é `3` e `1`.

- Qual deles é mais prioritário?
  - `1`
- Ele é mais prioritário que o pai?
  - Sim!

Trocamos o `1` com o pai dele `5`.

```
0              1
            __/ \__
         __/       \__
1       3             5
      _/ \_         _/ \_
2    7     4       2     6
```

Porém, ao fazermos isso, o `5` ficou acima do `2` e do `6`. Então vamos olhar novamente para o `2` e o `6`:

- Qual deles é mais prioritário?
  - `2`
- Ele é mais prioritário que o pai?
  - Sim!

Trocamos o `2` com o pai dele `5`.

```
0              1
            __/ \__
         __/       \__
1       3             2
      _/ \_         _/ \_
2    7     4       5     6
```

Como terminamos de descer, vamos voltar para onde estávamos antes: a segunda linha. Nela, não temos mais pares para verificar. Dessa forma, subimos novamente.

Agora estamos na raiz da árvore, o número `1`. Como não existe comparação aqui - nem com irmão, nem com pai, terminamos de ordenar.

Depois disso, vamos tirando o elemento do topo, ajustando a árvore, tirando o do topo de novo, assim por diante.

- pega o topo e adiciona na coleção {`1`}

```
0              ?
            __/ \__
         __/       \__
1       3             2
      _/ \_         _/ \_
2    7     4       5     6
```

- arruma a árvore

```
0              2
            __/ \__
         __/       \__
1       3             5
      _/ \_            \_
2    7     4             6
```

- pega o topo e adiciona na coleção {`1`, `2`}

```
0              ?
            __/ \__
         __/       \__
1       3             5
      _/ \_            \_
2    7     4             6
```

- arruma a árvore

```
0              3
            __/ \__
         __/       \__
1       4             5
      _/               \_
2    7                   6
```

- pega o topo e adiciona na coleção {`1`, `2`, `3`}

```
0              ?
            __/ \__
         __/       \__
1       4             5
      _/               \_
2    7                   6
```

- arruma a árvore

```
0              4
            __/ \__
         __/       \__
1       7             5
                       \_
2                        6
```

- pega o topo e adiciona na coleção {`1`, `2`, `3`, `4`}

```
0              ?
            __/ \__
         __/       \__
1       7             5
                       \_
2                        6
```

- arruma a árvore

```
0              5
            __/ \__
         __/       \__
1       7             6

-
```

- pega o topo e adiciona na coleção {`1`, `2`, `3`, `4`, `5`}

```
0              ?
            __/ \__
         __/       \__
1       7             6

-
```

- arruma a árvore

```
0              6
            __/
         __/
1       7

-
```

- pega o topo e adiciona na coleção {`1`, `2`, `3`, `4`, `5`, `6`}

```
0              ?
            __/
         __/
1       7

-
```

- arruma a árvore

```
0              7


-

-
```

- pega o topo e adiciona na coleção {`1`, `2`, `3`, `4`, `5`, `6`, `7`}

```
-


-

-
```

Paramos quando a árvore fica vazia. E, se olhar a coleção de números, agora ela está em ordem.


# Micro serviços

Divisão de um serviço em módulos, para rodar separado.

O termo para ter apenas um projeto centralizado que tem tudo dentro é Monolito.

Exemplo: um sistema de pagamentos. Uma possível divisão seria:
- Um micro serviço para fazer as transações
- Um micro serviço para as empresas se cadastrarem no sistema
- Um micro serviço para as empresas configurarem preferências no sistema
- Um micro serviço para o pessoal interno administrar o sistema


## Vantagens

A vantagem do micro serviço vem da independência de cada parte. Isso faz com que, se uma das partes começar a dar problema, o resto não seja afetado.

Além disso, quando você tem uma alteração em um micro serviço, você pode fazer o deploy apenas daquele micro serviço, ao contrário do modelo original, o monolito, em que você precisa fazer deploy do sistema todo.

Essa separação também possibilita que tenhamos tamanhos de infras diferentes para cada micro serviço. Por exemplo: transações podem ocorrer muitas por minuto, e ninguém quer ficar esperando muito a transação passar. Portanto é um micro serviço que precisa de uma infra robusta e extremamente tolerante a falha - se algo falhar, alguma coisa precisa imediatamente substituir esse algo.

Já o micro serviço que atende o pessoal interno que administra o sistema tem poucos acessos, não precisa atender tanta gente, por isso pode ser feita uma infra mais simples.

Mais uma vantagem é ter uma equipe mexendo apenas naquele micro serviço. Essa equipe não precisa conhecer o projeto como um todo para qualquer alteração que for ser feita. Novas pessoas entrando no projeto também aprenderão mais fácil a mexer nele. Projetos menores são mais fáceis de manter.


## Desvantagens

A desvantagem principal é quando tentamos dividir um projeto já pequeno em micro serviços. Todas as vantagens acima não são necessárias ao projeto pequeno pois, bem, ele é pequeno.

Todas as vantagens acima de tornariam desvantagens nesse caso. Ter vários projetos para gerenciar quando você poderia estar cuidando de um só, sem a chance de mudar uma regra em uma parte que possa impactar em outra parte.

Outro ponto é: com os micro serviços se comunicando entre si, temos mais tráfego de rede necessário para algo funcionar.

Também existe a necessidade de se estabelecer padrões de segurança para todos seguirem. Sem isso, algum dos micro serviços poderia estar mais aberto a ataques.


# Big O - O(1), O(n)...

É uma medida de "tempo" de um algoritmo. Porque "tempo", entre aspas? Computadores são diferentes e executam as mesmas operações em tempos diferentes. Não seria possível encontrar uma medida de tempo que atendesse a todos os computadores. Então foi criada uma medida que é baseada não no nosso tempo real, mas no número de operações que o computador precisará fazer.

Assim, de forma simplista, se um algoritmo A custa 3 operações, e no computador 1 eu levo 2 segundos para cada operação, dará um tempo de 6 segundos. Se em outro computador a operação levar 10 segundos, eu teria um tempo total de 30 segundos.

Porém a ideia central não é comparar computadores, e sim comparar algoritmos. Quero saber como fazer os processos mais rápido, seja meu computador bom ou ruim. Por isso a medida em operações é mais eficiente.

Se eu encontro um algoritmo B que resolve o mesmo problema, mas usa apenas 2 operações, no computador 1 (operação = 2 seg) vou levar 4 segundos, no computador 2 (operação = 10 seg) vou levar 20 segundos. Em qualquer dos dois computadores, eu fiz uma operação mais rápida.


## O que é o tal do "n"

Existem algoritmos que executam sempre no mesmo "tempo". Porém existem casos em que isso varia de acordo com o tamanho do problema que precisamos resolver. E esse tamanho é o nosso "n".

Exemplo: um livro com n páginas

- Você precisa pegar um livro da estante e colocar na sua cabeceira

O tempo gasto é constante, não importa o número de páginas: você só vai até a estante, pega o livro, vai até a cabeceira, pousa o livro ali e pronto.

- Você precisa ler o livro

Nesse caso, vai depender do número de páginas do livro para saber quanto tempo vai demorar. 20 páginas passam mais rápido que 200, se ambos os livros tiverem o mesmo nível de complexidade do tema para você.

Se estuda a complexidade de um algoritmo de forma a conseguir tornar os programas mais rápidos de serem executados.

Por exemplo, se você precisa ler o livro mais rápido, desenvolver uma forma de ler apenas as palavras chave e conseguir ainda sim entender o texto seria mais eficiente. Assim seria possível diminuir a complexidade do problema.

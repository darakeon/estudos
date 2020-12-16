## Índice (Index)

Índice é um recurso do banco de dados para tornar as buscas mais
rápidas.

Funciona como Índices e Sumários de livro: um lugar onde o banco de
dados pode procurar a posição exata daquele dado.

Quando você cria uma chave primária no banco de dados, o índice é criado
automaticamente. É como o índice em todo livro, onde você olha em qual
página está o capítulo procurado: você diz "quero os dados da linha de
ID 3" e o banco sabe onde encontrar, porque antes consulta o índice.

Alguns livros, além do índice, possuem um Sumário. É uma lista de
palavras, em geral no final do livro, para facilitar encontrar termos
comuns, por exemplo "Zeus" em um livro de mitologia grega. Ali se
encontram as palavras acompanhadas da lista de páginas onde elas podem
ser encontradas.

Da mesma forma, alguma outra coluna também pode ser muito usada em
consultas, por exemplo, uma chave estrangeira. Se temos uma tabela das
bibliotecas de São Paulo, e uma outra onde existem todos os livros de
cada biblioteca, quando for necessário listar os livros de uma
biblioteca, você vai consultar a tabela de livros, e pegar todos aqueles
que pertencem a biblioteca escolhida.

Pensando nisso, seria como olhar um Sumário: se você tiver um lugar para
consultar isso, você acharia os dados mais rápido. Para isso, você pode
usar índices também.

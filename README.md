## Salvar suas alterações no local 

- `git add`: adiciona quais alterações você quer.

```git add -p```

- `-p` é para ir te mostrando as alterações e escolhendo quais você irá fazer commit;
- desconsidera ARQUIVOS BINÁRIOS (ler mais a baixo sobre).

```git add .```

- `.` nos sistemas operacionais significa a pasta atual onde você está;
- com esse comando, todas as alterações nessa pasta e em suas subpastas são adicionadas.

```git add *file*```

- `*` para os sistemas significa qualquer coisa no caminho de um arquivo;
- com esse comando, qualquer arquivo que tenha a palavra ***file*** em seu nome ou em seu caminho será adicionado para fazer commit.

```git commit -m "sua mensagem de commit"```

- `git commit` empacota suas alterações para poder subir para o servidor;
- `-m` significa mensagem, que é o texto que vai descrever esse pacote;

## Olhar o que tem de alterações que ainda não foi commitado

```git status```

- mostra a lista de arquivos:
	- verdes: já foram adicionados pelo `git add`;
	- vermelhos: ainda estão sem adicionar.
  
```git diff```

- mostra as alterações **que ainda não passaram pelo** `git add`;
- desconsidera ARQUIVOS BINÁRIOS (ler mais a baixo sobre).

## ARQUIVOS BINÁRIOS

- São arquivos que não são de código:
	- IMAGENS;
	- ARQUIVOS DE BANCO DE DADOS (.db);
	- VÍDEOS ÁUDIOS;
	- ETC.
- Os comandos `git diff` ou `git add -p` desconsideram arquivos binários.
	- os dois mostram código fonte na tela do terminal, e não tem código fonte nesses arquivos.

## Atualizar o que tem local com o que tem no servidor

```git pull --all```

- `git pull` traz coisas do servidor;
- `--all` é para trazer de todas as branches.

## Trazer para a sua branch o que tem na branch master

```git rebase -i origin/master```

- `git rebase` faz uma branch pegar o que tem em outra;
- `-i` é de "interativo", faz com que abra uma janela e te mostre os commits que só tem na sua branch;
- `origin/master` é para dizer qual branch deve ser olhada (a master);

### Conflitos (conflicts)

- dar `git status`, isso vai mostrar arquivos que têm conflitos;
- abrir um arquivo que esteja com conflito;
- tem espaços com fundo azul e verde comparando alterações:
	- verificar quais alterações devem permanecer;
	- em cima, há links para decidir o que fazer, qual código aceitar.

```git rebase --continue```

- depois de resolvidos os conflitos, continua o processo de rebase.

## Subir o que você fez localmente

```git push```

- Sobe os commits que ainda estão apenas no seu computador;

```git push -u origin```

- `-u` serve para criar uma branch nova;
- `origin` é uma referência para o servidor, gitlab, github ou o que for.


## PERGUNTAS PENDENTES

- Por que maiúsculo?
- float? porque minúsculo?
- factor? porque minúsculo?
- porque parâmetro?
- chaves?
- return?

## REFERÊNCIAS

Estes exemplos usam uma loja de bolos para explicar POO.

### Quais são as separações lógicas no código?
- Projeto: lojas de bolos
- `src`: cozinha da loja
- `packages`: armários da cozinha (a primeira palavra começa com minúscula, as outras com maiúscula)
- tipo: qualquer recipiente (pode inclusive ser uma forma) (nativo, a escrita varia)
- classes: formas de bolos (todas as palavras começam com maiúscula)

### Herança

- classe mãe: uma forma que seria base para cozinhar os bolos:
- classes filhas: cada uma é uma peça que encaixa na "forma" (classe) mãe para fazer bolos diferentes, mas com a mesma base

- se a classe mãe for abstrata, quer dizer que só dá para cozinhar bolo usando a base (classe mãe) + uma peça (class filha)

### Visibilidade

- `public`: o que pode ser visto dentro dos outros packages (cobertura: visível para todo mundo)
- `private`: apenas dentro da classe (farinha: não podemos ver do lado de fora)
- `protected`: apenas quem herda a classe pode ver (recheio: o que vê dentro do bolo consegue ver o recheio)

### Outros itens

- variável: um ingrediente (a primeira palavra começa com minúscula, as outras com maiúscula)
- objeto: um bolo (a primeira palavra começa com minúscula, as outras com maiúscula)

- método: coisas que se faz com o objeto (a primeira palavra começa com minúscula, as outras com maiúscula)
```
bolo.morder()
bolo.jogarFora();
bolo.guardar();
```

- atributo: propriedades que o objeto tem (a primeira palavra começa com minúscula, as outras com maiúscula)
```
bolo.tamanho;
bolo.sabor;
bolo.dataValidade;
```

- import: pegar emprestado formas que não existem dentro daquela cozinha

- constructor: o ato de cozinhar o bolo (método que tem o mesmo nome da classe)

# Escrever um capítulo {#escrever-um-capitulo}

Cada capítulo é um arquivo `CHAPTER.md` numa pasta própria. A primeira linha, com um único `#`, vira o título no sumário. As seções usam `##` e `###`, e o sumário do PDF mostra até o terceiro nível.

## Abrir pelo que o leitor vai fazer

O primeiro parágrafo diz o que o leitor consegue fazer ao fim do capítulo. Em seguida, cada seção cumpre um passo. Um capítulo de guia costuma ter de três a cinco seções. Quando passa disso, provavelmente são dois capítulos.

## Listas e destaques

Use **negrito** para nomes de botões e comandos que o leitor procura na tela, e *itálico* para um termo que aparece pela primeira vez. Listas numeradas servem a passos em ordem:

1. Crie a pasta do capítulo em `capitulos/`.
2. Escreva o `CHAPTER.md` com o título na primeira linha.
3. Acrescente uma tabela `[[chapters]]` no `ebook.toml`, na posição de leitura.

Listas com marcadores servem a itens sem ordem:

- o título do capítulo;
- as seções com `##`;
- as figuras em `imagens/`.

> Uma citação em bloco reproduz um trecho de outra fonte. Registre a origem em `notas/fontes.md`.

## Código

Declare a linguagem do bloco para ativar o realce no PDF e no EPUB. Comandos de terminal usam `bash`:

```bash
ebookfy info
ebookfy build
```

Arquivos de configuração usam a linguagem do arquivo, como `toml` para a ficha do livro:

```toml
[output]
directory = "ebook"
formats = ["pdf", "epub", "mobi"]
```

No PDF, uma linha longa quebra sozinha no meio do comando, e quem copia o trecho leva a quebra junto. Mantenha cada linha com menos de 80 caracteres e divida comandos extensos com `\` no fim da linha.

## Notas de rodapé

As notas aparecem numeradas no texto.[^cap03-rotulos] No PDF, o texto da nota fica no pé da mesma página, como nesta. No EPUB, a chamada leva ao texto da nota e de volta, e o leitor digital mostra a nota numa janela ou no fim do capítulo.

Os rótulos valem para o livro inteiro, por isso cada capítulo usa o próprio prefixo, como `[^cap03-rotulos]` neste capítulo.

[^cap03-rotulos]: Dois capítulos com o mesmo rótulo, como `[^1]`, interrompem a compilação com a mensagem `Duplicate note reference`.

## Links

Links para sites funcionam nos três formatos, como a [página do Pandoc](https://pandoc.org/). Para levar o leitor a outro capítulo, use a âncora do título: volte a [Onde cada coisa fica](#onde-cada-coisa-fica) ou avance para [Compilar e conferir](#compilar-e-conferir).

A âncora é o título em letras minúsculas, sem acentos, com hífens no lugar dos espaços. Para não depender do texto do título, defina um identificador próprio, como este capítulo faz:

```markdown
# Escrever um capítulo {#escrever-um-capitulo}
```

Com o identificador, os links continuam funcionando mesmo que o título mude. Um link para o arquivo de outro capítulo, como `[ver](../06-compilar-e-conferir/CHAPTER.md)`, compila, mas fica quebrado na edição.

## O que fica de fora

O Ebookfy lê apenas o Markdown do capítulo. Um bloco de metadados YAML no topo do arquivo, entre linhas `---`, não vira ficha: ele aparece como texto no livro. Título, autoria e data ficam no `ebook.toml`.

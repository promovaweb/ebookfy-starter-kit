# Escrever um capítulo {#escrever-um-capitulo}

Cada capítulo é um arquivo `CHAPTER.md` numa pasta própria. A primeira linha, com um único `#`, vira o título no sumário. As seções usam `##` e `###`.

## Listas e destaques

Use **negrito** para nomes de botões e comandos que o leitor procura na tela, e *itálico* para um termo que aparece pela primeira vez.

1. Crie a pasta do capítulo em `capitulos/`.
2. Escreva o `CHAPTER.md` com o título na primeira linha.
3. Acrescente uma tabela `[[chapters]]` no `ebook.toml`, na posição de leitura.

> Uma citação em bloco serve para reproduzir um trecho de outra fonte. Registre a origem em `notas/fontes.md`.

## Código

Declare a linguagem do bloco para ativar o realce no PDF e no EPUB:

```toml
[[chapters]]
file = "capitulos/02-escrever-um-capitulo/CHAPTER.md"
```

## Notas de rodapé

As notas aparecem numeradas e levam o leitor ao texto da nota e de volta.[^cap02-rotulos] Os rótulos valem para o livro inteiro, por isso cada capítulo usa o próprio prefixo.

[^cap02-rotulos]: Dois capítulos com o mesmo rótulo, como `[^1]`, interrompem a compilação.

## Links

Links para sites funcionam nos três formatos, como a [página do Pandoc](https://pandoc.org/). Para levar o leitor a outro capítulo, use a âncora do título: volte a [Onde cada coisa fica](#onde-cada-coisa-fica) ou avance para [Compilar e conferir](#compilar-e-conferir). Um link para o arquivo de outro capítulo compila, mas fica quebrado na edição.

Este capítulo define o identificador `{#escrever-um-capitulo}` no título. Com ele, os links continuam funcionando mesmo que o título mude.

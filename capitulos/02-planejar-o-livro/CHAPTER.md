# Planejar o livro {#planejar-o-livro}

Um ebook curto fica pronto mais rápido quando o leitor e o resultado estão escritos antes do primeiro capítulo. O planejamento cabe em três arquivos da pasta `notas/`, que o compilador não lê. Eles servem a você e aos agentes que usam as skills do Ebookfy.

## Escrever o briefing

O briefing responde, em poucas linhas, para quem é o livro e o que essa pessoa consegue fazer depois de ler. Grave em `notas/briefing.md`:

```markdown
# Briefing · Meu primeiro ebook

Leitor: quem acabou de instalar o Ebookfy e nunca publicou um ebook.
Ponto de partida: sabe editar um arquivo de texto e abrir o terminal.
Resultado: compila um livro próprio em PDF, EPUB e MOBI e sabe conferir cada arquivo.
Tom: direto, em segunda pessoa, com um exemplo por recurso.
Formatos: PDF, EPUB e MOBI.
```

O resultado é a linha mais importante. Cada capítulo precisa levar o leitor um passo mais perto dele. Um capítulo que não ajuda nisso fica para outro livro.

## Apurar o que o livro afirma

Comandos, números e nomes de telas mudam de uma versão para outra. Antes de escrever, confira cada afirmação na fonte e registre em `notas/fontes.md` o que foi conferido, onde e quando. A skill `ebookfy-02-pesquisar` traz um modelo de ficha para isso.

> Uma afirmação sem fonte registrada volta para a apuração antes da revisão final.

## Montar o sumário

O sumário é a promessa do livro dividida em passos. Escreva em `notas/sumario.md` o título de cada capítulo e o que o leitor consegue fazer ao terminar a leitura dele:

| Capítulo | Ao terminar, o leitor consegue |
| --- | --- |
| Preparar a primeira edição | Abrir a ficha e listar os capítulos com `ebookfy info`. |
| Planejar o livro | Escrever o briefing e o sumário do próprio livro. |
| Escrever um capítulo | Usar listas, código, notas e links no Markdown. |
| Imagens e capa | Incluir figuras com legenda e configurar as capas. |
| Prefácio, créditos e autoria | Escrever os textos editoriais. |
| Compilar e conferir | Gerar os três formatos e conferir cada um. |
| Revisar e distribuir | Fechar a versão e entregar os arquivos certos. |

Títulos que dizem a ação, como *Compilar e conferir*, funcionam melhor que rótulos como *Compilação*. O leitor encontra o que procura no sumário do PDF e no índice do leitor digital.

## Criar as pastas

Com o sumário pronto, crie uma pasta por capítulo em `capitulos/`, com o número na frente para manter a ordem no explorador de arquivos. Depois, declare cada capítulo no `ebook.toml`, na ordem de leitura:

```toml
[[chapters]]
file = "capitulos/01-primeiro-capitulo/CHAPTER.md"

[[chapters]]
file = "capitulos/02-planejar-o-livro/CHAPTER.md"
```

O número da pasta não define a ordem do livro. Quem define é a sequência das tabelas `[[chapters]]`. Para trocar dois capítulos de lugar, troque as tabelas e renomeie as pastas para o explorador acompanhar.

# Preparar a primeira edição

Este livro de exemplo mostra, em três capítulos curtos, tudo o que o Ebookfy coloca numa edição: capa, sumário, figuras, tabelas, código, notas e links entre capítulos. Troque o texto pelo seu e compile para ver a mudança nos três formatos.

## Conferir a ficha

Abra o arquivo `ebook.toml` na raiz do livro. A tabela `[book]` guarda o título, a autoria, o idioma e a versão da edição. Troque `title` e `authors` pelos dados do seu livro e rode, na mesma pasta:

```bash
ebookfy info
```

O terminal mostra o título novo e a lista de capítulos na ordem das tabelas `[[chapters]]`.

![Livro aberto com marcador de página, a figura deste capítulo](imagens/livro.png){width=30%}

A figura acima mora em `imagens/`, ao lado deste `CHAPTER.md`. O texto entre colchetes aparece como legenda e também é lido por leitores de tela.

## Onde cada coisa fica

| Para alterar | Abra |
| --- | --- |
| Título, autoria, versão, formatos e ordem dos capítulos | `ebook.toml` |
| O texto de um capítulo e suas figuras | `capitulos/<pasta>/CHAPTER.md` e `imagens/` |
| Prefácio, créditos, autoria e capa | Os arquivos de `[files]`, em `editorial/` |
| Briefing, fontes, revisão e outros registros de trabalho | `notas/`, fora da edição |

No próximo capítulo, [Escrever um capítulo](#escrever-um-capitulo), você vê os recursos de texto que o compilador aceita.

---
name: ebookfy-13-exportar
description: Compila os formatos declarados e confere os exemplares em PDF, EPUB e MOBI. Use para gerar a edição ou investigar uma falha do conversor.
---

# Exportar e conferir a edição

Leia book.slug, book.version, output.directory e output.formats. Execute `ebookfy info --json` para conferir o projeto aberto. Confira a disponibilidade do Pandoc, do WeasyPrint para PDF e de ebook-convert para MOBI. O MOBI usa uma conversão intermediária para EPUB mesmo quando a entrega pede somente MOBI.

Na pasta da edição, execute `ebookfy build --json`. Confira o sucesso da execução e os caminhos em data.arquivos. Compare com os formatos solicitados. Para investigar uma falha, leia o primeiro erro do conversor, relacione-o ao arquivo de origem e repita a compilação após a correção.

Abra exemplares desta execução. Confira capa, sumário navegável nos leitores digitais, uma figura com legenda, acentos e último capítulo. Registre a versão da obra e os formatos realmente examinados.

## Referência de trabalho

Consulte [Prova dos três formatos](references/prova-dos-formatos.md) para localizar a causa de defeitos por formato.

## Checklist da entrega

- [ ] A pasta e o nome de cada saída correspondem à edição do TOML.
- [ ] Cada formato solicitado possui exemplar desta compilação.
- [ ] As provas abertas preservam texto, navegação e ilustrações nas páginas examinadas.

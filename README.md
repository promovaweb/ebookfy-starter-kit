![Ícone do Ebookfy](brand/logo/icon-48w.png)

# Ebookfy Starter Kit

Use este repositório privado como template para começar seu livro com a ficha, o primeiro capítulo ilustrado e as skills do [Ebookfy](https://github.com/promovaweb/ebookfy).

## Primeiro uso

Instale Node.js 22 ou superior, Pandoc, WeasyPrint e Calibre. Na raiz da sua cópia, execute os comandos abaixo.

```bash
npm install -g @promovaweb/ebookfy
ebookfy info
ebookfy build
```

Edite a ficha em [ebook.toml](ebook.toml), o [primeiro capítulo](capitulos/01-primeiro-capitulo/CHAPTER.md) e os arquivos em `editorial/`. Atualize a capa para a nova edição. Para acrescentar outro capítulo, crie sua pasta com `CHAPTER.md` e `imagens/` e acrescente uma tabela `[[chapters]]` na posição desejada. Execute `ebookfy` para conferir o sumário na TUI. Os arquivos compilados ficam no diretório definido em `output.directory`.

## Localizar os arquivos

| Para alterar | Abra |
| --- | --- |
| Título, autoria, versão, ordem e formatos | `ebook.toml` |
| Texto e imagens de um capítulo | `capitulos/<pasta>/CHAPTER.md` e a pasta irmã `imagens/` |
| Prefácio, capa digital, créditos e perfil de autoria | Os caminhos declarados em `[files]` |
| Preferências locais do terminal | `ebookfy config list` para consultar o perfil pessoal |
| Exemplares para leitura | A pasta de `output.directory` após `ebookfy build` |

## Trabalhar com agentes

Comece pela skill `ebookfy-01-organizar`. As skills instaladas estão em [.agents/skills](.agents/skills). Abra o SKILL.md da etapa, siga a referência local em `references/` e confira a entrega com a checklist. A [ficha de apuração](.agents/skills/ebookfy-02-pesquisar/references/ficha-de-apuracao.md) e a [prova dos três formatos](.agents/skills/ebookfy-13-exportar/references/prova-dos-formatos.md) mostram como registrar a fonte e conferir o exemplar. Os downloads do manual acompanham o [framework](https://github.com/promovaweb/ebookfy).

Consulte o [guia de contribuição](CONTRIBUTING.md), as [versões](CHANGELOG.md) e o [Discord da Promovaweb](https://promovaweb.com/discord).

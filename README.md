![Ícone do Ebookfy](brand/logo/icon-48w.png)

# Ebookfy Starter Kit

Use este repositório privado como ponto de partida para o seu livro. Ele traz a ficha, um livro de exemplo com sete capítulos, os textos editoriais e as 15 skills do [Ebookfy](https://github.com/promovaweb/ebookfy) instaladas para o seu agente.

## Primeiro uso

O jeito mais rápido é rodar `ebookfy init` num repositório Git vazio: o comando copia este modelo para a pasta. Se você criou a cópia direto pelo GitHub, instale Node.js 22 ou superior, Pandoc, WeasyPrint e Calibre e rode na raiz:

```bash
npm install -g @promovaweb/ebookfy
ebookfy doctor
ebookfy info
ebookfy build
```

O `doctor` confere os conversores e avisa quais formatos ficam indisponíveis quando falta algum. O `build` grava PDF, EPUB e MOBI em `ebook/`.

## O livro de exemplo

**Meu primeiro ebook** é um guia curto de produção que usa no próprio texto cada recurso que explica. Para ver como fica a edição compilada, com capa, sumário, figuras, notas e créditos, abra o [PDF](https://github.com/promovaweb/ebookfy/blob/main/ebook/primeiro-ebook-v0.1.0.pdf), o [EPUB](https://github.com/promovaweb/ebookfy/blob/main/ebook/primeiro-ebook-v0.1.0.epub) ou o [MOBI](https://github.com/promovaweb/ebookfy/blob/main/ebook/primeiro-ebook-v0.1.0.mobi) no repositório do Ebookfy.

| Capítulo | O que mostra |
| --- | --- |
| [Preparar a primeira edição](capitulos/01-primeiro-capitulo/CHAPTER.md) | A ficha, uma figura com legenda e a tabela de onde cada coisa fica. |
| [Planejar o livro](capitulos/02-planejar-o-livro/CHAPTER.md) | Briefing, apuração e sumário em `notas/`, com citação em bloco. |
| [Escrever um capítulo](capitulos/03-escrever-um-capitulo/CHAPTER.md) | Listas, código com realce, nota de rodapé e links entre capítulos. |
| [Imagens e capa](capitulos/04-imagens-e-capa/CHAPTER.md) | Figuras, formatos de imagem e as duas capas da edição. |
| [Prefácio, créditos e autoria](capitulos/05-abertura-e-fechamento/CHAPTER.md) | Os textos editoriais que abrem e fecham o livro. |
| [Compilar e conferir](capitulos/06-compilar-e-conferir/CHAPTER.md) | Conversores, mensagens de erro e a lista de conferência. |
| [Revisar e distribuir](capitulos/07-revisar-e-distribuir/CHAPTER.md) | Passadas de revisão, versão e entrega dos arquivos conferidos. |

Troque o texto pelo seu. Para acrescentar um capítulo, crie a pasta com `CHAPTER.md` e `imagens/` e acrescente uma tabela `[[chapters]]` na posição de leitura. Execute `ebookfy` para conferir o sumário na TUI.

## Onde editar

| Para alterar | Abra |
| --- | --- |
| Título, autoria, versão, ordem e formatos | [`ebook.toml`](ebook.toml) |
| Texto e imagens de um capítulo | `capitulos/<pasta>/CHAPTER.md` e a pasta irmã `imagens/` |
| Prefácio, capa digital, créditos e perfil de autoria | Os caminhos declarados em `[files]`, em `editorial/` |
| Briefing, fontes, revisão e outros registros de trabalho | [`notas/`](notas/README.md), fora da edição |
| Preferências locais do terminal | `ebookfy config list` para consultar o perfil pessoal |
| Exemplares para leitura | A pasta de `output.directory` depois de `ebookfy build` |

## Trabalhar com agentes

As skills instaladas ficam em [.agents/skills](.agents/skills). Comece pela `ebookfy-01-organizar`, que monta a ficha e o briefing do livro. Cada skill traz quando usar, o procedimento, as regras do compilador que afetam a etapa, uma tabela de problemas frequentes, uma checklist da entrega e referências com modelos preenchidos. As etapas combinam entre si pelos registros de `notas/`.

Para um livro que já existe em outro formato, comece pela `ebookfy-15-migrar`. Para uma tarefa pontual, entre direto na etapa: trocar uma figura começa na `ebookfy-05-imagens`; revisar antes de publicar, na `ebookfy-12-revisar`.

O manual completo do Ebookfy acompanha o [framework](https://github.com/promovaweb/ebookfy). Consulte também o [guia de contribuição](CONTRIBUTING.md), as [versões](CHANGELOG.md) e o [Discord da Promovaweb](https://promovaweb.com/discord).

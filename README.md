<p align="center">
  <a href="https://github.com/promovaweb/ebookfy">
    <img alt="Ebookfy" src="https://raw.githubusercontent.com/promovaweb/ebookfy-starter-kit/main/brand/logo/icon.png" width="112" height="112">
  </a>
</p>

<h1 align="center">Ebookfy Starter Kit</h1>

<p align="center">
  O ponto de partida do seu livro: ficha, livro de exemplo, textos editoriais e as 15 skills do Ebookfy instaladas para o seu agente.
</p>

<p align="center">Um projeto da <a href="https://promovaweb.com">Promovaweb</a></p>

<p align="center">
  <a href="https://github.com/promovaweb/ebookfy-starter-kit/releases/latest"><img alt="GitHub Release" src="https://img.shields.io/github/v/release/promovaweb/ebookfy-starter-kit"></a>
  <a href="LICENSE"><img alt="Licença" src="https://img.shields.io/github/license/promovaweb/ebookfy-starter-kit"></a>
</p>

<p align="center">
  <a href="https://promovaweb.com/discord"><img alt="Discord: obter ajuda e conversar com a Comunidade" src="https://img.shields.io/badge/Discord-Obter%20ajuda%20e%20conversar%20com%20a%20Comunidade-5865F2?style=for-the-badge&logo=discord&logoColor=white"></a>
</p>

<p align="center">
  <a href="https://github.com/promovaweb/ebookfy">Ebookfy</a> ·
  <a href="https://promovaweb.com/ferramentas/">Ferramentas</a> ·
  <a href="https://promovaweb.com/docs/">Documentação</a> ·
  <a href="https://promovaweb.com/harness/">Harness</a> ·
  <a href="https://promovaweb.com/discord">Discord</a> ·
  <a href="https://promovaweb.com/planos?utm_source=github&utm_medium=readme&utm_campaign=ebookfy-starter-kit">Planos da Promovaweb</a> ·
  <a href="CHANGELOG.md">Changelog</a>
</p>

## O que é

Este repositório é o modelo de livro do [Ebookfy](https://github.com/promovaweb/ebookfy), o CLI da Promovaweb que gera PDF, EPUB e MOBI a partir de capítulos Markdown. Ele traz a ficha `ebook.toml`, um livro de exemplo com sete capítulos, os textos editoriais e as 15 skills do Ebookfy instaladas para Claude Code, Codex e OpenCode.

## Primeiro uso

O jeito mais rápido é rodar `ebookfy init` num repositório Git vazio: o comando copia este modelo para a pasta. Você também pode clicar em **Use this template** no GitHub. Nos dois casos, instale [Node.js](https://github.com/nodejs/node) 22 ou superior, [Pandoc](https://github.com/jgm/pandoc), [WeasyPrint](https://github.com/Kozea/WeasyPrint) e [Calibre](https://github.com/kovidgoyal/calibre) e rode na raiz:

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

O manual completo acompanha o [Ebookfy](https://github.com/promovaweb/ebookfy), com a referência do CLI e as edições em PDF, EPUB e MOBI.

## Feito com

| Projeto | Para quê |
| --- | --- |
| [Ebookfy](https://github.com/promovaweb/ebookfy) | CLI que compila o livro e fonte das skills |
| [Pandoc](https://github.com/jgm/pandoc) | conversão para HTML e EPUB |
| [WeasyPrint](https://github.com/Kozea/WeasyPrint) | PDF |
| [Calibre](https://github.com/kovidgoyal/calibre) | MOBI |
| [skills](https://github.com/vercel-labs/skills) | instalação e atualização das skills nos agentes |

## Comunidade e suporte

- **Discord:** [obter ajuda e conversar com a Comunidade](https://promovaweb.com/discord).
- **Bugs e pedidos:** abra uma [issue](https://github.com/promovaweb/ebookfy-starter-kit/issues) com a versão, o sistema operacional e o passo a passo para reproduzir. Problemas do CLI vão para as [issues do Ebookfy](https://github.com/promovaweb/ebookfy/issues).
- **Novidades:** acompanhe o [CHANGELOG](CHANGELOG.md) e as [releases](https://github.com/promovaweb/ebookfy-starter-kit/releases).

## Contribuir

Leia o [guia de contribuição](CONTRIBUTING.md). O livro de exemplo e as skills nascem no [Ebookfy](https://github.com/promovaweb/ebookfy) e são copiados para cá.

## Promovaweb

O Ebookfy Starter Kit é mantido pela [Promovaweb](https://promovaweb.com), comunidade de co-working digital onde profissionais aprendem a construir, automatizar e gerir negócios de tecnologia e IA com aulas ao vivo, Co-works e revisão de projetos reais.

Quer escrever e publicar o seu livro com acompanhamento? Conheça os [planos da Promovaweb](https://promovaweb.com/planos?utm_source=github&utm_medium=readme&utm_campaign=ebookfy-starter-kit).

## Licença

Distribuído sob a [licença MIT](LICENSE), porque o starter kit é a base do livro de quem usa: o livro que você escreve a partir dele é seu e pode ter a licença ou os direitos autorais que você escolher. O [Ebookfy](https://github.com/promovaweb/ebookfy), com o CLI e as skills, segue sob a GNU AGPL 3.0. A licença não concede o uso do nome e do logo do Ebookfy nem da marca Promovaweb.

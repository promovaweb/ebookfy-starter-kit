# Mapa do projeto

## Árvore padrão

```text
meu-livro/
├── ebook.toml                      ficha da edição
├── capitulos/
│   ├── 01-instalar/
│   │   ├── CHAPTER.md              texto do capítulo
│   │   └── imagens/                figuras usadas só por este capítulo
│   └── 02-primeiro-fluxo/
│       ├── CHAPTER.md
│       └── imagens/
├── editorial/
│   ├── capa.png                    files.cover
│   ├── prefacio.md                 files.preface
│   ├── creditos.md                 files.credits
│   └── autor.md                    files.author
├── brand/logo/icon.png             files.logo (opcional)
├── notas/                          registros de trabalho, fora da leitura
│   ├── briefing.md                 etapa 01
│   ├── fontes.md                   etapa 02
│   ├── fontes/                     etapa 02, capturas e saídas de apoio
│   ├── sumario.md                  etapa 03
│   ├── atribuicoes.md              etapas 02, 05, 06 e 09
│   ├── revisao.md                  etapa 12
│   ├── entrega.md                  etapas 13 e 14
│   ├── build.json                  etapa 13, saída do build conferido
│   └── migracao.md                 etapa 15
├── ebook/                          output.directory, gerado pelo build
└── .agents/skills/                 skills instaladas pelo starter kit
```

O prefixo numérico da pasta ajuda a ler a árvore, mas a ordem de leitura vem só das tabelas `[[chapters]]`. Ao trocar dois capítulos de lugar, mova as tabelas; renomear as pastas é opcional.

A pasta `notas/` é uma convenção das skills, não do CLI. Ela guarda os registros que cada etapa produz e que a seguinte consulta. Nada ali é publicado, porque o compilador só lê os arquivos declarados no TOML e as imagens que esses arquivos referenciam. Se um capítulo apontar para uma imagem em `notas/`, ela entra na edição.

Se a pasta de saída não deve ir para o Git, acrescente `ebook/` ao `.gitignore`. Se a equipe distribui os exemplares pelo próprio repositório, mantenha a pasta versionada e registre a escolha no briefing.

## Campos da ficha

| Campo | Obrigatório | Formato e efeito |
| --- | --- | --- |
| `book.title` | sim | Título nos metadados, na capa e no rodapé do PDF. |
| `book.subtitle` | não | Linha abaixo do título no PDF. |
| `book.description` | sim | Texto de catálogo nos metadados do EPUB. |
| `book.language` | sim | Código de idioma, como `pt-BR`. Define hifenização e leitura em voz alta. |
| `book.authors` | sim | Lista com pelo menos um nome, na ordem de crédito. |
| `book.publisher` | sim | Editora ou organização responsável. |
| `book.rights` | sim | Declaração de direitos, como `© 2026 Ana Souza`. |
| `book.identifier` | sim | Identificador estável da obra, como `urn:editora:primeiros-fluxos-n8n` ou um ISBN. |
| `book.version` | sim | Edição no formato `X.Y.Z`. Entra no nome dos arquivos. |
| `book.date` | sim | Data da edição em `AAAA-MM-DD`. |
| `book.slug` | sim | Minúsculas sem acento, números e hífen. Forma `<slug>-v<version>.<formato>`. |
| `files.cover` | sim | Imagem da capa digital, PNG ou JPEG. |
| `files.logo` | não | Símbolo da composição A4 do PDF. |
| `files.preface` | sim | Markdown do prefácio, lido antes dos capítulos. |
| `files.credits` | sim | Markdown dos créditos, lido depois dos capítulos. |
| `files.author` | sim | Markdown da apresentação de autoria, lido por último. |
| `chapters.file` | sim, um ou mais | Caminho de um `CHAPTER.md` por tabela. |
| `output.directory` | sim | Pasta dos exemplares, relativa ao TOML. |
| `output.formats` | sim | Lista com `pdf`, `epub` e `mobi`, sem repetir. |

## Ficha preenchida

```toml
[book]
title = "Primeiros fluxos no n8n"
subtitle = "Automação para pequenos negócios"
description = "Da instalação ao primeiro fluxo que envia relatórios por email."
language = "pt-BR"
authors = ["Ana Souza"]
publisher = "Editora Exemplo"
rights = "© 2026 Ana Souza"
identifier = "urn:editora-exemplo:primeiros-fluxos-n8n"
version = "1.0.0"
date = "2026-11-23"
slug = "primeiros-fluxos-n8n"

[files]
cover = "editorial/capa.png"
logo = "brand/logo/icon.png"
preface = "editorial/prefacio.md"
credits = "editorial/creditos.md"
author = "editorial/autor.md"

[output]
directory = "ebook"
formats = ["pdf", "epub"]

[[chapters]]
file = "capitulos/01-instalar/CHAPTER.md"

[[chapters]]
file = "capitulos/02-primeiro-fluxo/CHAPTER.md"
```

Com essa ficha, `ebookfy build` grava `ebook/primeiros-fluxos-n8n-v1.0.0.pdf` e `ebook/primeiros-fluxos-n8n-v1.0.0.epub`.

## Reorganizar uma pasta existente

1. Rode `git status` e confirme que não há mudanças pendentes da pessoa. Se houver, pergunte antes de mover.
2. Liste o que existe e classifique cada arquivo: texto publicado, figura de capítulo, material editorial, nota de trabalho ou saída gerada.
3. Crie as pastas do mapa e mova cada arquivo com `git mv`.
4. Atualize os caminhos de imagem dentro dos capítulos movidos. O caminho de uma figura é relativo ao `CHAPTER.md` que a usa.
5. Rode `ebookfy info` e depois `ebookfy build` para confirmar que nada ficou apontando para o lugar antigo.

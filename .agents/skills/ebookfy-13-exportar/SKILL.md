---
name: ebookfy-13-exportar
description: Compila os formatos declarados no ebook.toml e confere os exemplares em PDF, EPUB e MOBI. Use para gerar a edição, investigar uma falha do build (pandoc, weasyprint, ebook-convert) ou conferir se um exemplar ficou correto antes da distribuição. Registra a prova em notas/entrega.md.
---

# Exportar e conferir a edição

Esta etapa transforma o manuscrito nos arquivos que o leitor vai abrir e confirma, olhando os arquivos, que eles estão certos. O build sem erro prova que os conversores rodaram; a conferência prova que a capa, o sumário, as figuras, os acentos e os links chegaram ao leitor.

## Quando usar

- Gerar a edição depois da revisão (etapa 12).
- Gerar uma prova intermediária para conferir figuras, tabelas ou capa.
- O build falhou e é preciso descobrir por quê.
- Mudou a versão de um conversor ou do Ebookfy e é preciso confirmar que a saída continua igual.

Passe para a etapa 14 com os exemplares conferidos. Volte à etapa de origem quando a conferência achar problema de conteúdo.

## Antes de começar

1. Rode `ebookfy doctor` e confira os conversores: `pandoc` é necessário para tudo, `weasyprint` para PDF e `ebook-convert` (Calibre) para MOBI. O doctor avisa quais formatos de `output.formats` ficam indisponíveis.
2. Rode `ebookfy info --json` e confira título, versão, formatos e a ordem dos capítulos.
3. Confira `book.version` e `book.date`: os dois aparecem na capa do PDF, e a versão entra no nome dos arquivos.

## Procedimento

1. **Compile.** Na raiz do livro, rode `ebookfy build --json | tee notas/build.json`. Leia `ok` e a lista `data.arquivos`. A etapa 14 usa esse arquivo para saber exatamente quais exemplares passaram pela prova.
2. **Se falhar, leia `error.message`.** Erros da ficha aparecem antes de qualquer conversão; erros de conversão começam com o nome do programa (`pandoc:`, `weasyprint:`, `ebook-convert:`). Use o [diagnóstico do build](references/diagnostico-do-build.md) para achar a causa, corrija na fonte e compile de novo.
3. **Confira os nomes.** Cada formato gera `<output.directory>/<slug>-v<version>.<formato>`. A lista deve ter exatamente os formatos de `output.formats`.
4. **Abra os arquivos desta execução.** Leitores guardam cópias importadas; abra os arquivos novos diretamente.
5. **Faça a prova de cada formato** seguindo a [prova dos formatos](references/prova-dos-formatos.md): capa, sumário, um capítulo com figura, tabela e código, uma nota de rodapé, um link interno, acentos, créditos e autoria.
6. **Registre a prova** em `notas/entrega.md`: versão, data, versões dos conversores (do `ebookfy doctor`), formatos examinados, leitores usados e o que foi visto.
7. **Decida o que fazer com os problemas.** Problema de conteúdo volta à etapa de origem; problema de formato (tabela larga demais no MOBI, figura grande) pode ser resolvido aqui com ajuste no Markdown ou na imagem.

## Como o build funciona

- O compilador lê prefácio, capítulos, créditos e autoria e os entrega ao Pandoc como um documento único, com sumário.
- O PDF passa por HTML com o kit de impressão A4 e é gerado pelo WeasyPrint.
- O EPUB é gerado pelo Pandoc com `files.cover` como capa.
- O MOBI é convertido do EPUB pelo `ebook-convert`. Por isso, pedir só MOBI ainda exige o Pandoc.
- Tudo é gerado numa pasta temporária dentro da saída e só é movido para o lugar final quando todas as conversões terminam. Se uma conversão falhar, os exemplares anteriores continuam intactos.
- Qualquer aviso do Pandoc é tratado como erro (`--fail-if-warnings`).

## Regras do Ebookfy que afetam esta etapa

- `output.directory` precisa ficar dentro da pasta do livro e não pode ser alcançada por link simbólico.
- Cada build grava datas internas nos arquivos, então duas compilações das mesmas fontes geram exemplares com hashes diferentes. Não recompile entre a prova e a distribuição; se recompilar, refaça a prova e o `notas/build.json`.
- Compilar a mesma versão de novo sobrescreve os arquivos dela. Para preservar uma edição distribuída, aumente `book.version` antes de compilar a próxima.
- `ebookfy build` sem `--json` imprime os caminhos gerados, um por linha.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| `pandoc: ... Could not fetch resource` | Figura ausente ou caminho errado. | Corrija o caminho relativo ao `CHAPTER.md`. |
| `pandoc: ... Duplicate note reference` | A mesma definição de nota (`[^1]:`) em dois arquivos. | Prefixe os rótulos com o capítulo. |
| `pandoc: ... ENOENT` ou "not found" | Pandoc não instalado. | Instale o Pandoc e confira com `ebookfy doctor`. |
| `weasyprint: ...` | WeasyPrint ausente ou falha ao montar o PDF. | Confira com `ebookfy doctor`; leia a linha seguinte do erro. |
| `ebook-convert: ...` | Calibre ausente ou falha na conversão. | Instale o Calibre com `ebook-convert` no PATH. |
| `A saída precisa ficar em uma pasta local do projeto.` | `output.directory` passa por link simbólico. | Use uma pasta real dentro do livro. |
| O leitor mostra a edição anterior. | Cópia antiga na biblioteca do leitor. | Remova a cópia e abra o arquivo novo. |

## Entrega

- Exemplares em `output.directory`, um por formato declarado.
- `notas/entrega.md` com a prova de cada formato.
- Problemas encontrados encaminhados às etapas de origem ou corrigidos, com nova compilação.

## Checklist da entrega

- [ ] `ebookfy doctor` mostra os conversores necessários para todos os formatos declarados.
- [ ] `ebookfy build --json` devolve `ok: true`, e a saída está em `notas/build.json`.
- [ ] `data.arquivos` tem exatamente um arquivo por formato de `output.formats`, com slug e versão corretos.
- [ ] Os arquivos conferidos são os desta execução, não cópias antigas.
- [ ] Capa, sumário, figuras, tabelas, código, notas, links internos e acentos foram conferidos em cada formato.
- [ ] Créditos e autoria aparecem no fim da edição.
- [ ] Quando há EPUB, os metadados (título, autoria, idioma) foram conferidos no leitor.
- [ ] `notas/entrega.md` registra versão, data, conversores, formatos e leitores usados.
- [ ] Problemas de conteúdo voltaram às etapas de origem.

## Referências

- [Prova dos formatos](references/prova-dos-formatos.md): o que conferir em PDF, EPUB e MOBI e modelo de registro.
- [Diagnóstico do build](references/diagnostico-do-build.md): mensagens de erro, causas e correções.

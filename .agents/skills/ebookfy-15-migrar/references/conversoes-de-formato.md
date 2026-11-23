# Conversões de formato

## O que converter

| Na origem | No Ebookfy | Como |
| --- | --- | --- |
| Frontmatter YAML (`title`, `author`, `date`, `lang`) | Campos de `[book]` | `title` vai para `book.title`, `author` para `book.authors` (sempre lista, mesmo com uma pessoa), `date` para `book.date` em `AAAA-MM-DD` e `lang` para `book.language`. Copiar as chaves com o nome original dá `Unrecognized key`. Depois, remova o bloco `---` de cada arquivo. |
| `reading-order.txt`, `SUMMARY.md` | Tabelas `[[chapters]]` na mesma ordem | Uma tabela por capítulo. |
| Manuscrito único | Um `CHAPTER.md` por título `#` | Divida nos títulos de primeiro nível, conferindo o mapa. |
| Seções `##` tratadas como capítulos | Seções dentro de um capítulo | Junte no capítulo a que pertencem. |
| Link para outro arquivo (`[ver](cap03.md)`) | Âncora (`[ver](#titulo-do-capitulo)`) | Troque pelo id do título ou defina `{#id}`. |
| Notas numeradas por capítulo (`[^1]`) | Rótulos únicos no livro (`[^cap03-1]`) | Prefixe com o capítulo. |
| Imagens numa pasta comum (`media/`, `assets/`) | `imagens/` de cada capítulo | Mova e corrija os caminhos. |
| Imagens remotas (`https://...`) | Arquivo local | Baixe, registre a origem na etapa 09 e use o caminho local. |
| HTML embutido (`<div>`, `<br>`, `<img>`) | Markdown | Converta; mantenha HTML só quando não houver equivalente e teste no MOBI. |
| Includes de outras ferramentas (`{{#include}}`, `!INCLUDE`) | Texto incorporado | Copie o conteúdo para o capítulo. |
| Comentários de revisão no texto | `notas/revisao.md` | Mova e remova do capítulo. |
| Créditos e biografia no fim do manuscrito | `files.credits` e `files.author` | Separe em `editorial/`. |

## DOCX

```bash
pandoc origem.docx -t gfm --wrap=none \
  --extract-media=notas/origem/media \
  -o notas/origem/manuscrito.md
```

Depois da conversão, confira:

- estilos de título do Word viraram `#`, `##`, `###` corretamente;
- listas numeradas mantêm a numeração;
- tabelas complexas (células mescladas) costumam virar HTML; simplifique;
- notas de rodapé viraram `[^n]`; prefixe por capítulo;
- imagens estão em `notas/origem/media/`, com nomes genéricos; renomeie ao mover.

## mdBook e GitBook

- `SUMMARY.md` dá a ordem. Itens aninhados costumam ser seções do capítulo pai.
- Links entre páginas (`[x](./cap/pagina.md)`) viram âncoras.
- `{{#include arquivo}}` precisa ser resolvido à mão.
- Admonitions (`> [!NOTE]`, `{% hint %}`) não têm estilo no kit; converta para parágrafo com **Nota:** em negrito.

## Projetos Pandoc com YAML

- O YAML de metadados vai para `[book]`.
- Opções de compilação (template, CSS) não migram; o Ebookfy usa o kit próprio.
- Filtros Lua não rodam; o que eles faziam precisa ser resolvido no texto.

## Livro só em PDF ou EPUB

Reaproveite apenas com autorização registrada. Para EPUB, extraia o HTML com `unzip` e converta cada arquivo com `pandoc -f html -t gfm`. Para PDF, a extração de texto perde estrutura; conte com revisão completa.

## Comandos de apoio

```bash
# títulos de primeiro nível do manuscrito, com linha
grep -n '^# ' notas/origem/manuscrito.md

# frontmatter restante nos capítulos
for f in capitulos/*/CHAPTER.md; do head -1 "$f" | grep -q '^---' && echo "$f"; done

# links que ainda apontam para arquivos .md
grep -rnE '\]\([^)#]*\.md(#[^)]*)?\)' capitulos/ editorial/

# imagens remotas, com ou sem extensão no endereço
grep -rnE '!\[[^]]*\]\(https?://' capitulos/ editorial/
```

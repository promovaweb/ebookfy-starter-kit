# Provas de capa

Depois de `ebookfy build`, confira cada formato com os arquivos recém-gerados em `output.directory`. Leitores digitais guardam cópias importadas; abra o arquivo novo diretamente, fora da biblioteca, ou remova a cópia antiga antes de importar.

## EPUB

1. Abra o EPUB num leitor que mostre a estante (Apple Books, Thorium, Calibre, KOReader).
2. Na estante, veja a miniatura: o título precisa ser lido sem abrir o livro.
3. Abra o livro: a capa deve aparecer inteira, sem faixas e sem corte.
4. Confira nos metadados do leitor o título, a autoria e o idioma.

## MOBI

1. Abra no Calibre (visualizador de ebooks) ou envie para um Kindle.
2. Confira a miniatura e a primeira tela. O Calibre reconverte a capa; cores muito saturadas podem mudar levemente.
3. No Kindle com tela de tinta eletrônica, a capa aparece em tons de cinza. Título com pouco contraste de luminosidade some.

## PDF

1. Abra a primeira página em 100%.
2. Confira, de cima para baixo: o símbolo (`files.logo`), a editora (`book.publisher`), o título, o subtítulo, a descrição, "Edição" com `book.version` e "Gerado em" com `book.date`.
3. Se o símbolo for a capa digital reduzida, falta `files.logo`.
4. Role até a segunda página e confira o sumário e o rodapé com o título e a numeração. A capa não tem rodapé. Em edições geradas antes do Ebookfy 0.5, o rodapé podia mostrar "Documento" no lugar do título.

## Tabela de diagnóstico

| O que se vê | Onde olhar | Ajuste |
| --- | --- | --- |
| EPUB com o título antigo na imagem | Arquivo apontado por `files.cover` | Refaça a arte e compile de novo. |
| Leitor mostra a edição anterior | Biblioteca do leitor | Remova a cópia importada e abra o arquivo novo. |
| Título encosta na borda da miniatura | Arquivo-fonte da arte | Aumente as margens seguras ou quebre o título em duas linhas. |
| Capa escura demais no Kindle | Contraste de luminosidade | Clareie o fundo ou escureça o título; teste em escala de cinza. |
| PDF com símbolo errado | `files.logo` | Corrija o caminho e compile. |
| PDF com descrição cortada ou empurrando a data | `book.description` | Encurte para uma ou duas frases. |

## Registro da prova

Anote na resposta à pessoa, ou em `notas/entrega.md` quando a capa fizer parte de uma edição:

```markdown
Capa conferida em 2026-11-23, edição 1.0.0:
- EPUB (Thorium): miniatura legível, capa inteira, metadados corretos.
- MOBI (Calibre 8.5): capa inteira; título legível em escala de cinza.
- PDF: símbolo, editora, título, subtítulo, edição 1.0.0 e data 2026-11-23 conferidos.
```

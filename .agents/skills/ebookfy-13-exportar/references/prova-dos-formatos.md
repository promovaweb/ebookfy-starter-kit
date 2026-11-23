# Prova dos formatos

> O modelo de registro usa um livro fictício, *Primeiros fluxos no n8n*.

## O que conferir em cada formato

| Item | PDF | EPUB | MOBI |
| --- | --- | --- | --- |
| Capa | Página tipográfica com símbolo, editora, título, subtítulo, edição e data. | Imagem de `files.cover` na estante e na abertura. | Imagem convertida; título legível em escala de cinza. |
| Sumário | Página de sumário com os títulos até o terceiro nível (`###`); níveis abaixo ficam só no corpo. | Navegação do leitor com os títulos na ordem. | Sumário do Kindle ou do Calibre. |
| Figura | Nítida em 100%, legenda embaixo. | Inteira com a fonte ampliada. | Visível; capturas pequenas continuam legíveis. |
| Tabela | Cabe na largura da página. | Não corta com a fonte ampliada. | Tabelas largas podem quebrar; confira a maior do livro. |
| Código | Realce, sem linhas cortadas na margem. | Quebra ou rolagem legível. | Fonte monoespaçada; linhas longas quebram. |
| Nota de rodapé | Numerada; o texto aparece no pé da página da chamada. | A nota abre; o retorno depende do recurso do leitor. | A nota abre; o retorno depende do aparelho. |
| Link interno | Leva à seção certa. | Leva à seção certa. | Leva à seção certa. |
| Acentos e símbolos | ç, ã, é, aspas e travessões corretos. | Idem. | Idem. |
| Rodapé | Título e numeração a partir da segunda página. | Não se aplica. | Não se aplica. |
| Fim da edição | Créditos e autoria. | Créditos e autoria. | Créditos e autoria. |

## Leitores para a prova

- **PDF:** qualquer leitor; confira em 100% e numa tela pequena.
- **EPUB:** Thorium, Apple Books, KOReader ou o visualizador do Calibre. Teste com a fonte ampliada em dois níveis e, se possível, no celular.
- **MOBI:** visualizador do Calibre ou um Kindle compatível, com o arquivo transferido por cabo. O envio por email (Send to Kindle) não aceita MOBI; para testar esse caminho, envie o EPUB.

Para conferir a estrutura do EPUB sem leitor:

```bash
unzip -l ebook/primeiros-fluxos-n8n-v1.0.0.epub
```

A lista mostra os capítulos (`EPUB/text/`), as imagens (`EPUB/media/`) e a capa.

## Escolha do capítulo de prova

Não é preciso ler a edição inteira em cada formato a cada build. Escolha:

- o capítulo com a maior tabela;
- o capítulo com mais figuras;
- o capítulo com o bloco de código mais longo;
- o primeiro e o último capítulo.

Na edição final, percorra o sumário inteiro em cada formato.

## Modelo de registro

Grave em `notas/entrega.md`:

```markdown
## Prova · edição 1.0.0 · 2026-11-23

Conversores (ebookfy doctor): pandoc 3.10.2, WeasyPrint 69.0, ebook-convert (calibre 8.5.0).
Comando: ebookfy build --json, ok: true.

Arquivos:
- ebook/primeiros-fluxos-n8n-v1.0.0.pdf
- ebook/primeiros-fluxos-n8n-v1.0.0.epub

PDF (Evince, 100%):
- Capa com símbolo, editora, título, subtítulo, edição 1.0.0 e data conferidos.
- Sumário com 7 capítulos, créditos e autoria.
- Cap. 04: tabela de colunas da planilha cabe na página; figura legível.

EPUB (Thorium, fonte +2):
- Capa e miniatura legíveis.
- Navegação com todos os títulos.
- Cap. 03: link para "Ajustar o fuso horário" leva à seção certa.
- Nota de rodapé do cap. 05 abre; o leitor oferece o retorno.

Pendências: nenhuma.
```

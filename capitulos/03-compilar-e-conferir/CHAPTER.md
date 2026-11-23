# Compilar e conferir {#compilar-e-conferir}

Com a ficha e os capítulos prontos, gere os formatos declarados em `output.formats`. Antes, confira se os conversores estão instalados:

```bash
ebookfy doctor
ebookfy build
```

O `doctor` mostra a versão do Pandoc, do WeasyPrint e do `ebook-convert`, e avisa quando falta um deles. O `build` grava os arquivos na pasta `ebook/`, com o slug e a versão no nome, como `ebook/primeiro-ebook-v0.1.0.epub`.

## O que conferir

Abra os arquivos recém-gerados e confira:

- [ ] a capa do EPUB e a página de capa do PDF;
- [ ] o sumário, com os três capítulos na ordem;
- [ ] a figura e a tabela do primeiro capítulo;
- [ ] a nota de rodapé e os links do segundo capítulo;
- [ ] os créditos e a apresentação de autoria no fim.

Se o build falhar, a primeira linha da mensagem diz qual programa falhou. Uma figura com o caminho errado, por exemplo, aparece como `pandoc: [WARNING] Could not fetch resource`.

## Próximo passo

Troque este exemplo pelo seu livro. As skills em `.agents/skills/` guiam cada etapa, da organização à distribuição. Comece por `ebookfy-01-organizar`.

# Capturas e formatos

## Formato por tipo de imagem

| Tipo | Formato | Motivo |
| --- | --- | --- |
| Captura de tela | PNG | Texto e bordas nítidos, sem artefatos de compressão. |
| Fotografia | JPEG, qualidade 80 a 85 | Arquivo bem menor que PNG para a mesma aparência. |
| Diagrama com formas e texto | SVG ou PNG | SVG fica nítido em qualquer zoom; PNG é mais previsível no MOBI. |
| Ícone dentro do texto | PNG pequeno | Evite; prefira o nome do ícone em texto. |
| WebP, HEIC, GIF animado | Converter | Suporte irregular nos leitores digitais e no MOBI. |

## Tamanho

- Capturas: 1200 a 1800 px de largura depois do recorte. Menos que isso fica borrado no PDF; mais que isso só pesa.
- Fotos: até 1600 px no lado maior.
- Peso: mire em até 300 KB por figura. Um livro com 40 capturas de 2 MB vira um EPUB de 80 MB.
- Para reduzir PNG sem perder nitidez, use uma ferramenta sem perda, como `oxipng`. O `pngquant` reduz bem mais, mas com perda por quantização de cores: compare o resultado com o original antes de trocar.

## Como capturar uma tela

1. **Ambiente de demonstração.** Use um projeto ou conta criado para o livro, com nomes e dados fictícios: `Loja Exemplo`, `ana@exemplo.com`. Nunca capture a conta real de alguém.
2. **Estado certo.** A tela deve estar exatamente no ponto descrito pelo texto: o painel aberto, o campo preenchido com o valor do exemplo.
3. **Tamanho da janela.** Uma janela de 1280 a 1440 px de largura com zoom de 100 a 125% produz texto legível depois do recorte.
4. **Tema.** Prefira o tema claro. Capturas escuras ficam pesadas no papel e destoam do fundo branco do PDF. Se o livro inteiro usar tema escuro, mantenha em todas.
5. **Recorte.** Corte até o elemento principal e o contexto mínimo para o leitor achá-lo na própria tela: o painel e o título dele, não a janela inteira.
6. **Destaque, quando necessário.** Um retângulo ou seta numa cor só, sempre a mesma no livro inteiro. Não use desfoque para esconder dados: troque os dados.
7. **Consistência.** Mesmo navegador, mesmo tema, mesmo zoom em todas as capturas do livro.

## Capturas de terminal

Prefira bloco de código a captura de terminal. O leitor pode copiar o texto, o leitor de tela consegue ler e o arquivo é menor.

````markdown
```text
$ ebookfy info
Primeiros fluxos no n8n
Ana Souza
1. Instalar o n8n e abrir o editor
2. Montar o primeiro fluxo
```
````

Use captura só quando cores, layout ou interface de terminal (TUI) forem o assunto.

## Diagramas

- Desenhe com poucas cores e texto em tamanho próximo ao do corpo do livro depois de reduzido à largura da coluna.
- Exporte em SVG com textos convertidos em contorno, ou em PNG a 2x.
- Guarde o arquivo editável (por exemplo `.drawio` ou `.excalidraw`) em `notas/figuras/`, fora da edição, para atualizar depois.

## Teste de legibilidade

Depois do build, abra:

1. o PDF em 100% de zoom: o texto da captura deve ser lido sem ampliar;
2. o EPUB num leitor com a fonte ampliada em dois níveis: a figura deve continuar inteira, sem corte;
3. o MOBI no Calibre ou num Kindle, quando o formato for entregue.

Se o detalhe principal sumir em qualquer um, recorte mais, aumente o zoom da captura ou transforme os rótulos essenciais em texto no parágrafo.

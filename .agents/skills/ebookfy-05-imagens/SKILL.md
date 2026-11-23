---
name: ebookfy-05-imagens
description: Prepara, insere, troca ou corrige figuras dos capítulos (capturas de tela, fotos, diagramas) com legenda útil, tamanho legível nos três formatos e origem registrada. Use quando um capítulo precisa de imagem, quando uma figura some ou fica ilegível no PDF, EPUB ou MOBI, ou quando o build falha ao ler uma imagem.
---

# Preparar imagens dos capítulos

Esta etapa garante que cada figura mostre ao leitor o detalhe de que ele precisa, continue legível numa tela de celular e numa página A4, e tenha origem conhecida. A figura mora na pasta do capítulo que a usa e entra no texto com uma legenda que diz o que observar.

## Quando usar

- O roteiro do capítulo prevê figuras ou a redação mostrou que um passo precisa ser visto.
- Uma interface mudou e as capturas ficaram desatualizadas.
- O build falha com `Could not fetch resource`.
- A figura aparece borrada, cortada ou minúscula em algum formato.
- Chegou uma imagem de terceiro para entrar no livro.

Passe para a etapa 09 com a origem de toda figura que não foi produzida pela equipe. Use a etapa 06 para a capa: ela tem regras próprias.

## Antes de começar

1. Leia a passagem que a figura vai acompanhar e o roteiro em `notas/sumario.md`.
2. Confira se a figura é necessária. Se o texto já descreve o passo sem ambiguidade, uma captura a mais só alonga a página.
3. Abra `notas/atribuicoes.md` para registrar a origem.

## Procedimento

1. **Defina o que o leitor precisa ver.** Escreva em uma frase: "o campo Trigger at Hour com o valor 9". Essa frase guia o enquadramento e vira a base da legenda.
2. **Produza ou obtenha a imagem.** Siga o [guia de capturas e formatos](references/capturas-e-formatos.md): projeto de demonstração com dados fictícios, janela no tamanho certo, tema claro, zoom que deixa o texto legível.
3. **Recorte para o detalhe.** Corte barras, abas e áreas vazias que não ajudam a achar o elemento. Uma captura da tela inteira com um botão pequeno no canto não ensina nada no celular.
4. **Escolha o formato e o tamanho.** PNG para capturas e diagramas com texto, JPEG para fotografias, SVG para diagramas vetoriais. Largura entre 1200 e 1800 px para capturas, até 300 KB por arquivo sempre que possível.
5. **Nomeie e guarde.** Salve em `capitulos/<pasta>/imagens/` com nome descritivo em minúsculas e hífen: `schedule-trigger-semanal.png`. Nada de `image1.png` ou `Captura de tela 2026-11-20.png`.
6. **Insira no texto** como parágrafo próprio, com legenda que diz o que observar. Siga o [guia de legendas](references/legendas-e-texto-alternativo.md). Se a captura for pequena, limite a largura com `{width=60%}`.
7. **Diga no texto o que a figura mostra.** O leitor de tela, o MOBI com imagem desligada e quem pulou a figura precisam conseguir seguir o passo só pelo texto.
8. **Registre a origem** em `notas/atribuicoes.md`: arquivo, autor ou ferramenta que gerou, data, licença ou autorização.
9. **Confira nos formatos.** Rode `ebookfy build` e abra a página no PDF em 100%, no EPUB com a fonte ampliada e, se houver MOBI, num leitor Kindle ou no Calibre. O detalhe da frase do passo 1 precisa ser legível nos três.

## Regras do Ebookfy que afetam esta etapa

- O caminho é relativo ao `CHAPTER.md`: `![Legenda](imagens/arquivo.png)`.
- Guarde a imagem em `imagens/` do capítulo. O `ebookfy build` recusa caminho para fora do livro e endereço `https://` antes de chamar o Pandoc, com exit code 3 e uma linha por imagem (`capitulos/02-x/CHAPTER.md:14 usa https://... (endereço remoto)`). Baixe a imagem, registre a origem e use o caminho relativo.
- Imagem ausente, nome com caixa diferente ou extensão errada fazem o build falhar com `Could not fetch resource`. Em Linux, `Figura.PNG` e `figura.png` são arquivos diferentes.
- Uma imagem sozinha no parágrafo vira figura com legenda. O texto entre colchetes aparece embaixo da imagem e também serve de texto alternativo.
- Uma imagem dentro de uma frase fica inline, sem legenda.
- O EPUB embute cópias das imagens; uma figura de 5 MB deixa o livro pesado para baixar e abrir.
- WebP compila, mas leitores antigos e o MOBI podem não exibir. Converta para PNG ou JPEG.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| `Could not fetch resource capitulos/.../imagens/x.png` | Arquivo ausente, nome ou caixa diferente. | Liste a pasta `imagens/` e copie o nome exato para o Markdown. |
| A figura aparece sem legenda e sem texto alternativo. | Colchetes vazios: `![](imagens/x.png)` não vira figura. | Escreva a legenda dizendo o que observar. |
| A legenda impressa é o nome do arquivo. | O nome do arquivo foi escrito entre os colchetes. | Troque pela frase que diz o que observar. |
| Texto da captura ilegível no celular. | Captura da tela inteira em resolução alta e reduzida. | Recorte a região relevante ou aumente o zoom antes de capturar. |
| Captura pequena esticada e borrada no PDF. | Imagem de baixa largura ocupando a coluna inteira. | Use `{width=50%}` ou capture com mais resolução. |
| A figura aparece no meio da frase. | Imagem sem linha em branco antes e depois. | Coloque a imagem num parágrafo próprio. |
| Dado pessoal visível na captura. | Captura feita numa conta real. | Refaça com dados fictícios ou cubra a área antes de salvar. |
| SVG sem texto no MOBI. | Fonte do SVG não disponível no leitor. | Converta os textos em contorno ou exporte em PNG. |

## Entrega

- Figuras em `capitulos/<pasta>/imagens/` com nomes descritivos e tamanho adequado.
- Referências no `CHAPTER.md` com legenda que diz o que observar e texto que descreve o passo.
- `notas/atribuicoes.md` com a origem de cada figura.
- Build sem aviso e as figuras conferidas nos formatos declarados.

## Checklist da entrega

- [ ] Cada figura tem uma frase que diz o que o leitor precisa ver, e o enquadramento mostra esse detalhe.
- [ ] A imagem está na pasta `imagens/` do capítulo que a usa, com nome descritivo em minúsculas.
- [ ] O formato é PNG, JPEG ou SVG, e o arquivo tem tamanho razoável para o EPUB.
- [ ] A legenda diz o que observar; não repete o nome do arquivo nem começa com "Imagem de".
- [ ] O texto do capítulo permite seguir o passo mesmo sem ver a figura.
- [ ] A captura usa dados fictícios e não expõe nomes, emails, tokens ou endereços reais.
- [ ] A origem de cada figura está registrada em `notas/atribuicoes.md`.
- [ ] `ebookfy build` termina sem aviso.
- [ ] A figura foi conferida em cada formato de `output.formats` (no EPUB, com fonte ampliada); o detalhe principal está legível.
- [ ] Capturas antigas substituídas foram removidas da pasta com `git rm`.

## Referências

- [Capturas e formatos](references/capturas-e-formatos.md): como capturar telas, escolher formato e tamanho, e preparar diagramas.
- [Legendas e texto alternativo](references/legendas-e-texto-alternativo.md): como escrever a legenda, com exemplos bons e ruins.

# Imagens e capa {#imagens-e-capa}

Uma figura bem escolhida poupa um parágrafo de explicação. Neste capítulo, você inclui figuras com legenda e configura as duas capas da edição: a do leitor digital e a página de abertura do PDF.

## Incluir uma figura

Guarde a imagem na pasta `imagens/` do capítulo e escreva a referência com o caminho relativo ao `CHAPTER.md`:

```markdown
![Capa do PDF deste livro, gerada pelo Ebookfy](imagens/capa-do-pdf.png){width=55%}
```

Uma imagem sozinha no parágrafo vira uma figura com legenda. O texto entre colchetes cumpre duas funções: aparece embaixo da imagem e é lido em voz alta pelos leitores de tela. Escreva o que a figura mostra, numa frase completa.

![Capa do PDF deste livro, gerada pelo Ebookfy a partir da ficha](imagens/capa-do-pdf.png){width=55%}

A figura acima é a primeira página do PDF que você está lendo, exportada como imagem.

## Escolher o formato da imagem

| Conteúdo | Formato | Observação |
| --- | --- | --- |
| Captura de tela, diagrama, símbolo | PNG | Mantém letras e linhas nítidas. |
| Fotografia | JPEG | Arquivo menor, sem perda visível. |
| Ilustração vetorial | PNG exportado do SVG | O MOBI não exibe SVG em todos os aparelhos. |

Capturas de tela ficam legíveis com 1200 pixels de largura. Recorte a área que importa e confira o tamanho do texto no PDF antes de seguir. Imagens de terceiros só entram com a licença registrada em `notas/atribuicoes.md`.

O compilador interrompe o build quando uma imagem não existe no caminho indicado. A mensagem traz `Could not fetch resource` e o nome do arquivo.

## As duas capas

A edição tem duas capas, e cada uma vem de um lugar:

- **Capa digital**: a imagem de `files.cover`, usada no EPUB e no MOBI. É ela que aparece na estante do leitor digital e na loja.
- **Capa do PDF**: uma página tipográfica montada pelo compilador com o símbolo de `files.logo`, a editora, o título, a descrição, a versão e a data da compilação.

```toml
[files]
cover = "editorial/capa.png"
logo = "brand/logo/icon.png"
```

A capa digital funciona melhor em formato retrato, na proporção de 1600 por 2560 pixels, com o título legível na miniatura da estante. A capa do PDF não precisa de imagem própria: troque o título, a descrição e a versão na ficha e compile de novo.

Sem `files.logo`, o compilador usa a capa digital reduzida no lugar do símbolo. O resultado costuma ficar pequeno demais, por isso vale declarar um símbolo quadrado.

## Conferir as imagens na edição

Depois do build, abra o PDF e o EPUB lado a lado e confira em cada figura:

- a imagem certa no lugar certo;
- a legenda completa embaixo;
- o texto da imagem legível no tamanho da página;
- a largura adequada no leitor digital, onde a tela é menor.

# Especificações da capa

## Dimensões

| Item | Valor recomendado |
| --- | --- |
| Proporção | 1:1,6 (largura : altura) |
| Tamanho | 1600 × 2560 px; mínimo 1000 × 1600 px |
| Cor | RGB (sRGB). CMYK é para gráfica, não para ebook. |
| Formato | JPEG com qualidade 85 para arte com foto; PNG para arte chapada |
| Peso | Menos de 1 MB |
| Margem segura | 8% em cada lado; nenhum texto fora dela |

## Hierarquia

1. **Título.** O maior elemento, legível numa miniatura de 150 px de largura. Na prática, ocupa de 60 a 90% da largura da arte.
2. **Subtítulo.** Bem menor que o título; pode ficar ilegível na miniatura sem prejuízo.
3. **Autoria.** Nome na grafia de `book.authors`, abaixo ou acima do título.
4. **Marca da editora.** Discreta, num canto ou no rodapé.
5. **Edição.** Só quando importa para o leitor ("2ª edição", "Edição 2027"). Lembre de atualizar a cada versão.

## Tipografia

- Use uma ou duas famílias. Títulos ganham com peso forte (bold, black).
- Fontes muito finas somem na miniatura e na tinta eletrônica.
- Confirme a licença da fonte para uso em imagem comercial e registre em `notas/atribuicoes.md`. Fontes sob a SIL Open Font License permitem esse uso.

## Contraste

- Título sobre fundo com contraste alto. Teste convertendo a arte em escala de cinza: se o título perde força, o Kindle com tela de tinta vai perder também.
- Texto sobre foto precisa de uma área calma da imagem ou de uma faixa de cor por trás.

## Fotos e ilustrações

- Use apenas imagens com origem registrada: foto própria, banco com licença explícita, ilustração encomendada com contrato.
- Guarde o original em alta resolução e o arquivo editável da arte em `notas/capa/`, fora da edição, para refazer a composição depois.
- Se a pessoa fornece uma foto, confirme a área que pode ser cortada e a grafia do crédito.

## Símbolo do PDF (`files.logo`)

- Quadrado, fundo transparente, PNG ou SVG.
- Pelo menos 512 × 512 px no PNG.
- Funciona sobre fundo branco: o PDF tem página de capa clara.

## Exemplo de briefing de capa

```markdown
Capa · Primeiros fluxos no n8n · edição 1.0.0
- Título: Primeiros fluxos no n8n
- Subtítulo: Automação para pequenos negócios
- Autoria: Ana Souza
- Marca: símbolo da Editora Exemplo no rodapé
- Visual: fundo laranja chapado, ilustração de três nodes ligados, título em branco
- Fontes: Manrope ExtraBold (título), Inter Regular (subtítulo), ambas SIL OFL
- Ilustração: feita pela equipe, arquivo editável em notas/capa/capa.excalidraw
- Aprovação: Marcos
```

---
name: ebookfy-06-capa
description: Prepara a capa digital do EPUB e do MOBI e confere a capa tipográfica que o kit compõe no PDF. Use ao criar a primeira capa, quando título, subtítulo, autoria, marca ou edição mudarem, ou quando a capa aparecer cortada, ilegível ou diferente entre os formatos.
---

# Compor a capa

O Ebookfy tem duas capas diferentes, e esta etapa cuida das duas. A capa digital é uma imagem (`files.cover`) usada como capa do EPUB e do MOBI e como miniatura nas estantes dos leitores. A capa do PDF é composta pelo kit de impressão a partir dos dados da ficha. Uma mudança no título exige conferir as duas.

## Quando usar

- Primeira edição do livro, depois que título e autoria foram confirmados.
- Mudança de título, subtítulo, autoria, editora, marca ou versão destacada na arte.
- A miniatura fica ilegível na estante do leitor ou a capa aparece cortada.
- O PDF mostra a imagem da capa reduzida no lugar do símbolo.

Volte à etapa 01 se título e autoria ainda não estiverem confirmados. Registre a origem de fotos, ilustrações e fontes da arte e passe para a etapa 09.

## Antes de começar

1. Leia `[book]` na ficha: `title`, `subtitle`, `authors`, `publisher`, `version`, `description`.
2. Leia `[files]`: `cover` e `logo`.
3. Confirme no briefing quem aprova a capa.

## Como cada formato usa a capa

| Formato | O que aparece | De onde vem |
| --- | --- | --- |
| EPUB | A imagem de `files.cover` como capa e miniatura. | Arquivo de imagem. |
| MOBI | A mesma imagem, convertida pelo Calibre. | Arquivo de imagem. |
| PDF | Página tipográfica: símbolo, editora, título, subtítulo, descrição, "Edição X.Y.Z" e "Gerado em" com a data. | `files.logo` (ou `files.cover` sem logo) e os campos de `[book]`. |

O PDF não imprime a imagem da capa digital como página inteira e não mostra `book.authors` na capa. A autoria aparece nos metadados do arquivo e no texto de `files.author`. A partir da segunda página, o rodapé mostra o título e a numeração; a capa não tem rodapé.

## Procedimento

1. **Confirme os textos da capa.** Título e subtítulo exatamente como em `[book]`. Nome de autoria na grafia aprovada.
2. **Desenhe a capa digital** seguindo as [especificações da capa](references/especificacoes-da-capa.md): proporção 1:1,6 (por exemplo 1600 × 2560 px), título legível na miniatura, margens seguras, RGB.
3. **Escolha o ativo visual** com origem conhecida: arte da equipe, foto própria, banco de imagens com licença registrada ou ilustração encomendada. Registre em `notas/atribuicoes.md`.
4. **Exporte** em JPEG (foto) ou PNG (arte chapada) e salve em `editorial/capa.jpg` ou `editorial/capa.png`. Aponte `files.cover` para o arquivo.
5. **Defina o símbolo do PDF.** Aponte `files.logo` para o símbolo da editora ou do projeto, quadrado e com fundo transparente. Sem `files.logo`, o kit coloca a capa digital inteira, reduzida, no espaço do símbolo.
6. **Revise os campos que o PDF usa.** `publisher` aparece acima do título, `subtitle` abaixo, `description` em seguida, depois versão e data. Uma descrição longa demais empurra o resto da página.
7. **Compile e confira** com as [provas de capa](references/provas-de-capa.md): miniatura no leitor de EPUB, capa no Calibre ou Kindle, primeira página do PDF.
8. **Atualize a cada edição.** Se a arte mostra número de edição ou ano, troque junto com `book.version`.

## Regras do Ebookfy que afetam esta etapa

- `files.cover` é obrigatório e precisa existir dentro do livro.
- `files.logo` é opcional. Quando presente, também precisa existir.
- O título do PDF e dos metadados vem de `book.title`. Texto escrito na imagem não atualiza a ficha, nem o contrário.
- A data impressa no PDF é `book.date`. Atualize a cada edição.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| A capa digital inteira aparece pequena no topo do PDF. | `files.logo` ausente. | Aponte `files.logo` para o símbolo quadrado. |
| Título ilegível na estante do leitor. | Fonte fina ou pequena, pouco contraste. | Aumente o título até ocupar boa parte da largura e use contraste alto. |
| Capa com faixas pretas ou cortada. | Proporção diferente de 1:1,6. | Reexporte em 1600 × 2560 px ou proporção equivalente. |
| A capa mostra o título antigo. | Imagem não foi refeita depois da mudança na ficha. | Refaça a arte e compile de novo. |
| O PDF mostra a data errada. | `book.date` não foi atualizado. | Atualize a data na ficha. |
| Leitor recusa ou demora a abrir o EPUB. | Capa com vários MB. | Reduza para menos de 1 MB. |

## Entrega

- Capa digital em `editorial/`, apontada por `files.cover`.
- Símbolo apontado por `files.logo`.
- Origem dos ativos da capa em `notas/atribuicoes.md`.
- Conferência das três provas registrada na resposta, com o que foi visto em cada formato.

## Checklist da entrega

- [ ] Título, subtítulo e autoria da arte batem com `[book]` e com a grafia aprovada.
- [ ] A imagem tem proporção próxima de 1:1,6 e pelo menos 1600 px de largura.
- [ ] O título é legível na miniatura (cerca de 150 px de largura).
- [ ] O arquivo está em JPEG ou PNG, em RGB, com menos de 1 MB.
- [ ] `files.logo` aponta para um símbolo quadrado, ou a pessoa aceitou a capa reduzida no PDF.
- [ ] `book.description` cabe na página de capa do PDF sem empurrar a versão e a data.
- [ ] Fotos, ilustrações e fontes da arte têm origem e licença em `notas/atribuicoes.md`.
- [ ] A capa foi conferida em cada formato de `output.formats`.
- [ ] Número de edição ou ano na arte batem com `book.version` e `book.date`.
- [ ] Quem aprova a capa recebeu a prova.

## Referências

- [Especificações da capa](references/especificacoes-da-capa.md): dimensões, margens, tipografia e hierarquia.
- [Provas de capa](references/provas-de-capa.md): como conferir cada formato e o que procurar.

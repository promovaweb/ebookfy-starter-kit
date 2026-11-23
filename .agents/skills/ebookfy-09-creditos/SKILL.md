---
name: ebookfy-09-creditos
description: Consolida atribuições, licenças e permissões no arquivo de créditos apontado por files.credits. Use antes de distribuir uma edição, quando entrar imagem, fonte, citação ou contribuição de terceiro, ou quando uma figura não tiver origem conhecida. Reconcilia notas/atribuicoes.md, a ficha e os arquivos realmente usados.
---

# Conferir os créditos

Esta etapa garante que tudo que o livro usa de outra pessoa tem origem conhecida, condição de uso documentada e crédito na forma pedida pela fonte. O resultado é o texto de créditos da edição e um registro de atribuições que bate com os arquivos realmente incluídos.

## Quando usar

- Antes de cada distribuição, como conferência obrigatória.
- Sempre que uma figura, foto, ilustração, fonte tipográfica, citação longa, tabela ou trecho de código de terceiro entrar no livro.
- Quando a revisão encontrar uma figura sem origem.
- Quando mudarem autoria, revisão, edição ou outras participações.

As etapas 02, 05 e 06 alimentam `notas/atribuicoes.md`. A etapa 10 cuida da apresentação de autoria; esta etapa cuida das participações e das fontes.

## Antes de começar

1. Leia `[book]`: `authors`, `publisher`, `rights`.
2. Abra `notas/atribuicoes.md` e o arquivo de `files.credits`.
3. Liste os arquivos que a edição usa: capa, símbolo, figuras de todos os capítulos.

## Procedimento

1. **Levante o que a edição usa.** Liste as imagens referenciadas nos capítulos e em `[files]`. Um jeito rápido: procure `](imagens/` em todos os `CHAPTER.md` e some `files.cover` e `files.logo`. Inclua as fontes tipográficas da capa e do kit de impressão.
2. **Reconcilie com o registro.** Para cada arquivo, confira se há linha em `notas/atribuicoes.md`. Use o [registro de atribuição](references/registro-de-atribuicao.md). Arquivo sem linha é pendência. Cada linha precisa corresponder a algo em uso na edição: um arquivo, um trecho citado, uma fonte tipográfica, uma participação ou uma autorização (como a de um prefácio convidado). Remova a linha só depois de confirmar que o material saiu da edição.
3. **Confira a condição de uso.** Para cada material de terceiro: licença (com versão, como CC BY 4.0), autorização por escrito ou termo do banco de imagens. Leia se a licença permite uso comercial, adaptação e distribuição no formato e no canal da edição.
4. **Copie o crédito exigido.** Muitas licenças e autorizações pedem uma forma específica de crédito: nome, link, título da obra, indicação de alteração. Use exatamente essa forma.
5. **Separe as participações.** Autoria do texto, organização, revisão técnica, revisão de texto, capa, ilustrações, fotografia, diagramação. Use os nomes na grafia que cada pessoa aprovou.
6. **Compare com a ficha.** `book.authors` lista quem assina; `book.publisher` e `book.rights` precisam bater com o que os créditos dizem.
7. **Trate as pendências.** Material sem autorização ou com licença incompatível não entra na edição distribuída: substitua, peça autorização ou remova. Registre a escolha e avise a pessoa responsável.
8. **Escreva os créditos** em `files.credits` seguindo os [modelos de créditos](references/modelos-de-creditos.md).
9. **Leia na prova.** Compile e leia a página de créditos no PDF e no EPUB. Links devem abrir e nomes devem estar junto da obra certa.

## Regras do Ebookfy que afetam esta etapa

- O arquivo vem de `files.credits` e é lido depois do último capítulo e antes da autoria.
- Precisa existir e começar com um título `#`, que aparece no sumário.
- O kit de impressão do PDF usa as famílias Inter e Manrope, sob a SIL Open Font License. Mantenha esse crédito quando o PDF for distribuído.
- `book.rights` vai para os metadados do EPUB. Escreva a declaração completa, como `© 2026 Ana Souza. Todos os direitos reservados.`

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| Figura sem origem conhecida. | Imagem copiada de busca ou de material antigo. | Encontre a origem ou substitua por figura própria. |
| Licença CC BY-NC num livro vendido. | Licença não comercial. | Peça autorização ou troque a imagem. |
| Crédito com nome diferente do pedido pela fonte. | Crédito reescrito de memória. | Copie a forma exigida pela licença ou autorização. |
| Créditos citam figura removida do livro. | Registro não acompanhou a edição. | Reconcilie o registro com os arquivos usados. |
| `book.rights` diz uma coisa e os créditos outra. | Ficha e texto editados separadamente. | Alinhe os dois. |

## Entrega

- `files.credits` atualizado, com participações, fontes de imagens, tipografia e licenças.
- `notas/atribuicoes.md` reconciliado com os arquivos da edição.
- Lista de pendências e o que foi feito com cada uma, comunicada à pessoa.

## Checklist da entrega

- [ ] Toda imagem referenciada nos capítulos e em `[files]` tem linha em `notas/atribuicoes.md`.
- [ ] Nenhuma linha do registro aponta para arquivo que saiu da edição.
- [ ] Cada material de terceiro tem licença ou autorização compatível com o uso e o canal da edição.
- [ ] Os créditos usam a forma exigida pela fonte, com nome, link e indicação de alteração quando pedida.
- [ ] Participações estão separadas por função, com a grafia aprovada por cada pessoa.
- [ ] `book.authors`, `book.publisher` e `book.rights` batem com os créditos.
- [ ] O crédito das fontes tipográficas do PDF está presente.
- [ ] Materiais sem autorização foram substituídos ou removidos antes da distribuição.
- [ ] A página de créditos foi lida em cada formato de `output.formats`, com links abrindo.

## Referências

- [Registro de atribuição](references/registro-de-atribuicao.md): formato de `notas/atribuicoes.md` e exemplos por tipo de material.
- [Modelos de créditos](references/modelos-de-creditos.md): estrutura do texto de créditos e formas de crédito por licença.

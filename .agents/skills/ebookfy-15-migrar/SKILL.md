---
name: ebookfy-15-migrar
description: Migra para o Ebookfy um livro que já existe em outro formato (manuscrito único em Markdown ou DOCX, coleção de arquivos com reading-order, projeto de outra ferramenta). Use como porta de entrada para um acervo existente, preservando a ordem de leitura, as figuras, os links e a rastreabilidade entre a origem e o novo projeto em notas/migracao.md.
---

# Migrar um livro existente

Esta etapa leva um livro pronto, ou quase pronto, para a estrutura do Ebookfy sem perder nada no caminho. O trabalho é mecânico, mas cheio de detalhes: títulos que viram capítulos, figuras com caminhos antigos, links que atravessavam arquivos, notas de pesquisa misturadas ao texto. Um mapa de migração registra de onde veio cada trecho.

## Quando usar

- Manuscrito único (um `.md` grande, um `.docx`) que precisa ser dividido em capítulos.
- Coleção de arquivos com ordem declarada (`reading-order.txt`, `SUMMARY.md`, índice numerado).
- Projeto de outra ferramenta (mdBook, GitBook, Pandoc com YAML, pasta de capítulos sem ficha).
- Livro publicado em PDF ou EPUB cujo original se perdeu, quando houver autorização para reaproveitar o texto.

Depois da migração, siga para a etapa 01 (conferir ficha e briefing), 12 (revisão) e 13 (exportação). Se a migração mostrar que a ordem precisa mudar, passe pela etapa 03.

## Antes de começar

1. Trabalhe numa cópia. Guarde a origem intacta fora da pasta do novo livro: o `ebookfy init` só aceita pasta vazia.
2. Confirme com a pessoa quais arquivos são texto publicado e quais são notas, rascunhos ou material descartado.
3. Gere, se possível, uma edição de referência da origem (PDF ou EPUB) para comparar no fim.

## Procedimento

1. **Crie a estrutura** com `ebookfy init` em repositório vazio, ou manualmente seguindo a árvore da etapa 01. Copie então a origem para `notas/origem/`, fora de `[[chapters]]`.
2. **Converta o que não for Markdown.** Se a origem for DOCX, gere `notas/origem/manuscrito.md` com o comando das [conversões de formato](references/conversoes-de-formato.md) e trabalhe a partir dele.
3. **Descubra a ordem de leitura.** Procure ordem explícita: `reading-order.txt`, `SUMMARY.md`, índice, numeração de arquivos. Em manuscrito único, os títulos de primeiro nível costumam marcar capítulos.
4. **Monte o mapa** em `notas/migracao.md` seguindo o [mapa de migração](references/mapa-de-migracao.md): para cada trecho, origem (arquivo e título), destino (pasta e `CHAPTER.md`), posição e observações. Inclua prefácio, créditos, autoria e o que fica de fora.
5. **Divida e mova o texto.** Um `CHAPTER.md` por capítulo, cada um com um único `#`. Preserve blocos de código, notas, tabelas e citações exatamente; não reescreva durante a migração.
6. **Separe os materiais editoriais.** Prefácio, créditos e autoria vão para `editorial/` e para `[files]`. Capa para `files.cover`.
7. **Leve as figuras.** Cada imagem vai para `imagens/` do capítulo que a usa. Atualize os caminhos para `imagens/arquivo.png`. Imagem usada por dois capítulos é copiada para os dois.
8. **Converta o que o Ebookfy não lê.** Siga a [tabela de conversões](references/conversoes-de-formato.md): frontmatter YAML vira campos do TOML, links entre arquivos viram âncoras, rótulos de nota ganham prefixo, HTML vira Markdown quando possível.
9. **Preserve as notas de trabalho** em `notas/`: pesquisa, pautas, comentários de revisão. Nada disso entra em `[[chapters]]`.
10. **Monte a ficha.** Preencha `[book]` a partir dos metadados da origem e do briefing. Declare os capítulos na ordem do mapa.
11. **Confira pelo CLI.** `ebookfy info` deve listar os capítulos na ordem do mapa. `ebookfy build` deve terminar sem aviso; cada falha aponta um caminho ou referência que ainda precisa de ajuste.
12. **Compare com a origem.** Abra a nova edição ao lado da de referência. Confira o primeiro, o último e dois capítulos do meio: início e fim de cada um, figuras, tabelas, notas. Conte capítulos e figuras nos dois lados.
13. **Registre o resultado** no mapa: trechos migrados, duplicações removidas, lacunas, passagens que pedem revisão editorial.

## Regras do Ebookfy que afetam esta etapa

- Um `CHAPTER.md` por capítulo, cada um numa pasta própria, cada um com um único `#`.
- Frontmatter YAML não é lido e vira texto na edição.
- Link para outro arquivo de capítulo fica quebrado na edição; use âncoras.
- O livro é compilado como documento único: rótulos de nota e ids explícitos precisam ser únicos na obra.
- Imagens remotas e caminhos para fora do livro não são recusados pelo CLI, mas tornam o build dependente de rede e da máquina. Traga todas as figuras para `imagens/` dos capítulos.
- Prefácio, créditos e autoria são obrigatórios em `[files]`. Se a origem não tiver algum deles, crie um arquivo curto e registre no mapa que ele precisa de texto.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| Muitos `Could not fetch resource` no primeiro build. | Caminhos de imagem da origem. | Mova cada figura para `imagens/` do capítulo e corrija o caminho. |
| `Duplicate note reference` | Cada capítulo da origem numerava notas a partir de 1. | Prefixe os rótulos com o capítulo. |
| Texto `title:` no começo dos capítulos. | Frontmatter da origem. | Leve os dados para o TOML e remova o bloco. |
| Capítulo some ou aparece duas vezes. | Mapa não bate com `[[chapters]]`. | Confira tabela por tabela contra o mapa. |
| Seções viraram capítulos. | Divisão por `##` em vez de `#`. | Junte as seções no capítulo correto. |
| Notas de revisão aparecem no livro. | Comentários deixados no texto. | Mova para `notas/revisao.md`. |

## Entrega

- Projeto Ebookfy com ficha válida, capítulos em pastas, figuras locais e materiais editoriais.
- `notas/migracao.md` com o mapa completo e o resultado da comparação.
- Origem preservada para consulta.
- Lista de lacunas e passagens que seguem para revisão (etapa 12).

## Checklist da entrega

- [ ] A origem está preservada e intacta.
- [ ] O mapa registra origem, destino e posição de cada trecho, inclusive do que ficou de fora.
- [ ] Cada capítulo tem pasta própria, `CHAPTER.md` e um único título `#`.
- [ ] Prefácio, créditos e autoria estão em `[files]`.
- [ ] Todas as figuras estão na pasta `imagens/` do capítulo que as usa.
- [ ] Não há frontmatter YAML, link para `CHAPTER.md` nem rótulo de nota repetido entre capítulos.
- [ ] Notas de trabalho estão em `notas/` e fora de `[[chapters]]`.
- [ ] `ebookfy info` lista os capítulos na ordem do mapa.
- [ ] `ebookfy build` termina sem aviso.
- [ ] A nova edição foi comparada com a origem: contagem de capítulos e figuras e leitura de início e fim de capítulos escolhidos.
- [ ] Lacunas e passagens para revisão estão registradas.

## Referências

- [Mapa de migração](references/mapa-de-migracao.md): formato de `notas/migracao.md` com um exemplo preenchido.
- [Conversões de formato](references/conversoes-de-formato.md): o que converter de cada origem e comandos úteis.

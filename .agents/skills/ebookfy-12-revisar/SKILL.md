---
name: ebookfy-12-revisar
description: Revisa a edição por leitura integral na ordem do livro e pela reprodução dos exemplos. Use antes da exportação final, depois de mudanças grandes ou quando a pessoa pedir uma revisão de um ou mais capítulos. Diagnostica passagens com local, efeito no leitor e correção, aplica as correções quando autorizado e registra tudo em notas/revisao.md.
---

# Revisar o manuscrito

A revisão lê o livro como o leitor vai ler: na ordem, do prefácio à autoria, executando os exemplos. Ela encontra saltos, termos usados antes de explicados, exemplos que não funcionam, afirmações sem fonte e referências quebradas. Uma compilação sem erro não é revisão: ela só confirma que os arquivos foram processados.

## Quando usar

- Antes da exportação da edição que será distribuída.
- Depois de reorganizar capítulos, trocar a versão de uma ferramenta ou receber texto de outra pessoa.
- Quando a pessoa pede revisão de um capítulo ou do livro.

Correções de conteúdo voltam às etapas de origem: fonte (02), capítulo (04), figura (05), créditos (09). Passe para a etapa 13 quando não houver achado aberto que impeça a edição.

## Antes de começar

1. Pergunte, se não estiver claro: o pedido é só diagnóstico ou inclui correção? Revisão do livro todo ou de capítulos específicos?
2. Rode `ebookfy info` para ter a ordem exata.
3. Abra `notas/revisao.md` no formato do [registro de revisão](references/registro-de-revisao.md).
4. Tenha o ambiente dos exemplos pronto: versões do briefing, dados de demonstração.

## Procedimento

1. **Leia na ordem da edição:** prefácio, capítulos na ordem de `[[chapters]]`, créditos, autoria. Numa revisão parcial, declare no registro o que foi lido e o que ficou de fora.
2. **Primeira passada: percurso.** Leia sem parar para corrigir vírgulas. Marque onde o leitor travaria: termo novo sem explicação, passo que depende de algo não feito, resultado não descrito, capítulo que não encaixa no anterior.
3. **Segunda passada: exemplos.** Execute cada comando e procedimento na ordem do texto, num ambiente limpo. Registre entrada e resultado observado.
4. **Terceira passada: fontes.** Para cada afirmação verificável, confira se há entrada em `notas/fontes.md`. Afirmação sem fonte vira achado.
5. **Quarta passada: mecânica.** Títulos (`#` único por arquivo), âncoras de links internos, caminhos de figuras, legendas, notas de rodapé, tabelas, blocos de código com linguagem. Use a [lista de passadas](references/passadas-de-revisao.md).
6. **Registre cada achado** com arquivo, trecho curto, o que acontece com o leitor, correção proposta e gravidade (`impede`, `atrapalha`, `ajuste`).
7. **Corrija, se autorizado.** Edite a passagem e repita a verificação que revelou o problema: reexecute o exemplo, releia a transição, recompile. Marque o achado como `corrigido` só depois disso.
8. **Compile e leia uma prova.** `ebookfy build` sem aviso. Abra o PDF e o EPUB e leia ao menos o sumário, um capítulo com figura e tabela, os créditos.
9. **Entregue o registro.** Achados corrigidos, achados abertos com responsável, o que foi lido e o que foi executado.

## Regras do Ebookfy que afetam esta etapa

- A ordem da edição é: `files.preface`, capítulos na ordem de `[[chapters]]`, `files.credits`, `files.author`.
- O build falha em qualquer aviso do Pandoc. Figura ausente, nota duplicada e id repetido aparecem como erro; link para âncora inexistente ou para outro arquivo não gera aviso e só aparece na prova.
- Links para `CHAPTER.md` compilam e ficam quebrados na edição. Procure `](../` e `CHAPTER.md)` nos capítulos.
- Títulos repetidos em capítulos diferentes ganham sufixo no id, e um link sem id explícito pode cair no capítulo errado.
- Frontmatter YAML vira texto solto na edição.

## Problemas frequentes

| Achado | Onde costuma estar | Correção |
| --- | --- | --- |
| Termo usado antes de explicado. | Capítulos movidos de lugar. | Traga a explicação para o primeiro uso. |
| Exemplo falha com a versão atual da ferramenta. | Capturas e comandos antigos. | Reproduza, atualize texto, figura e ficha de fontes. |
| "Como vimos no capítulo 3" depois de reordenar. | Referência por número. | Cite pelo título e com link de âncora. |
| Link interno leva ao lugar errado. | Títulos repetidos sem id explícito. | Defina o id no título e use-o no link: `## Destino {#alvo}` e `[Ir](#alvo)`. |
| Figura com legenda que não diz o que observar. | Etapa 05 pulada. | Reescreva a legenda. |
| Tom muda entre capítulos. | Capítulos escritos por pessoas ou momentos diferentes. | Alinhe ao tom do briefing. |

## Entrega

- `notas/revisao.md` com escopo, achados, correções e verificações.
- Correções aplicadas, quando autorizado, com a verificação repetida.
- Build sem aviso e a prova lida.
- Resumo para a pessoa: quantos achados por gravidade, quais foram corrigidos, quais seguem abertos e o que impede a distribuição.

## Checklist da entrega

- [ ] O escopo está declarado: o que foi lido, o que foi executado, o que ficou de fora.
- [ ] A leitura seguiu a ordem da edição.
- [ ] Cada achado tem arquivo, trecho, efeito no leitor, correção e gravidade.
- [ ] Todos os exemplos do escopo foram executados, com entrada e resultado registrados.
- [ ] Afirmações sem fonte foram registradas como achado.
- [ ] Links internos usam âncoras e levam ao lugar certo.
- [ ] Cada achado `corrigido` teve a verificação repetida depois da correção.
- [ ] `ebookfy build` termina sem aviso.
- [ ] Sumário, um capítulo com figura e tabela e os créditos foram lidos em cada formato de `output.formats`.
- [ ] Achados abertos têm responsável e estão comunicados.

## Referências

- [Registro de revisão](references/registro-de-revisao.md): formato de `notas/revisao.md` com achados preenchidos.
- [Passadas de revisão](references/passadas-de-revisao.md): o que procurar em cada passada e comandos para achar problemas mecânicos.

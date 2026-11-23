---
name: ebookfy-04-capitulos
description: Escreve, expande ou reorganiza um CHAPTER.md a partir do roteiro e das fontes apuradas. Use para redigir um capítulo novo, reescrever um capítulo fraco, dividir ou fundir capítulos, ou mover um capítulo de lugar. Cobre estrutura, exemplos reproduzíveis, Markdown aceito pelo compilador e links entre capítulos.
---

# Escrever e reorganizar capítulos

Esta etapa produz o texto que o leitor vai ler. Um bom capítulo começa onde o anterior parou, leva o leitor a fazer algo concreto e termina num resultado que ele reconhece. Tudo que o capítulo afirma vem de `notas/fontes.md`, e todo exemplo foi executado.

## Quando usar

- Redigir um capítulo previsto em `notas/sumario.md`.
- Reescrever um capítulo que a revisão marcou como confuso, vago ou incompleto.
- Dividir um capítulo longo, fundir dois capítulos ou mudar um capítulo de posição.

Volte à etapa 02 se uma afirmação necessária não tiver fonte. Volte à etapa 03 se o capítulo depender de algo que nenhum capítulo anterior entrega. Use a etapa 05 para preparar as figuras e a 07 para a abertura do primeiro capítulo.

## Antes de começar

1. Leia o roteiro do capítulo em `notas/sumario.md`: pergunta, pré-requisitos, ação e resultado.
2. Leia as entradas de `notas/fontes.md` indicadas no roteiro.
3. Leia o fim do capítulo anterior e o começo do seguinte. O capítulo precisa encaixar nos dois.
4. Releia o tom definido em `notas/briefing.md`: tratamento, formalidade e termos técnicos.

## Procedimento

1. **Abra pela situação do leitor.** O primeiro parágrafo diz onde ele está (o que já tem do capítulo anterior) e o que vai conseguir ao fim deste. Sem histórico do assunto e sem definição de dicionário.
2. **Apresente só o que será usado.** Cada termo novo aparece quando o leitor precisa dele, com uma frase de explicação.
3. **Mostre uma execução completa.** Siga a [anatomia do capítulo](references/anatomia-do-capitulo.md): preparação, passos, resultado esperado, variação ou erro comum. Em comandos, diga a pasta de execução, o comando exato e o que deve aparecer.
4. **Descreva o resultado observável.** O leitor precisa saber que deu certo: a mensagem que aparece, o arquivo que surge, o número que muda.
5. **Feche ligando ao próximo.** Um parágrafo que resume o que o leitor tem agora e por que isso importa no capítulo seguinte. Sem resumo em lista do que acabou de ser dito.
6. **Escreva no Markdown aceito.** Use os recursos da [referência de Markdown](references/markdown-do-ebookfy.md): um único `#`, seções em `##` e `###`, blocos de código com linguagem, tabelas simples, figuras locais, links internos por âncora.
7. **Faça a leitura de iniciante.** Releia como alguém que só leu os capítulos anteriores. Marque todo nome que aparece só numa figura, todo passo implícito e todo "simplesmente". Corrija no texto.
8. **Reproduza os exemplos.** Execute cada comando e procedimento na ordem do texto, num ambiente limpo quando possível. Se algo mudou, corrija o texto e a ficha de fontes.
9. **Confira pelo CLI.** `ebookfy info` mostra o título na posição certa. `ebookfy build` compila sem aviso. Abra o capítulo no PDF ou no EPUB e leia as figuras, tabelas e blocos de código.

## Reorganizar capítulos

- **Mover:** troque a posição da tabela `[[chapters]]`. Revise a abertura e o fechamento do capítulo movido e dos vizinhos, porque as pontes mudam.
- **Dividir:** crie a pasta nova, mova as seções e as figuras que ela usa, acrescente a tabela e escreva abertura e fechamento para as duas partes.
- **Fundir:** traga o texto e as imagens para uma pasta, remova a tabela da outra e apague a pasta antiga com `git rm` depois de conferir que nada mais aponta para ela.
- Em todos os casos, procure links internos (`](#`) que apontavam para títulos alterados e atualize as âncoras.

## Regras do Ebookfy que afetam esta etapa

- O título do capítulo é o primeiro `#` do arquivo. Um segundo `#` cria outra entrada de primeiro nível no sumário.
- Não use frontmatter YAML. O compilador não lê o bloco como metadado: as linhas entre `---` são interpretadas como Markdown comum e podem aparecer como texto, linha horizontal ou até tabela, inclusive no fim da seção anterior.
- Caminhos de imagens são relativos ao próprio `CHAPTER.md`: `![...](imagens/arquivo.png)`.
- Imagem ausente ou caminho errado derruba o build, porque o compilador falha em qualquer aviso do Pandoc. O build também recusa imagem com caminho fora do livro ou endereço remoto; guarde todas em `imagens/` do capítulo.
- Link para outro arquivo (`../02-x/CHAPTER.md`) compila, mas fica quebrado no EPUB e no PDF. Entre capítulos, use a âncora do título: `[Agendar a execução](#agendar-a-execução)`, ou defina um id explícito com `{#agendar}`.
- O livro inteiro é compilado como um documento só. Títulos iguais em capítulos diferentes recebem sufixo (`exemplo`, `exemplo-1`), e um link para `#exemplo` leva sempre ao primeiro. Seções que recebem link precisam de id explícito.
- Rótulos de nota de rodapé também valem para o livro inteiro. Duas definições `[^1]:` em capítulos diferentes derrubam o build com `Duplicate note reference`. Prefixe com o capítulo: `[^cap03-limite]`.
- Links externos (`https://...`) funcionam nos três formatos.
- HTML embutido passa para o EPUB e o PDF, mas costuma quebrar o MOBI. Prefira Markdown puro.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| `Inclua um título de nível 1` | O arquivo não tem nenhum `#`, só `##`, ou o único `#` está dentro de bloco de código. | Abra com `# Título do capítulo`. |
| O capítulo aparece duas vezes no sumário. | Há dois títulos `#` no arquivo. | Rebaixe o segundo para `##`. |
| `Could not fetch resource capitulos/...` | Imagem com caminho errado, caixa diferente ou ausente. | Confira o nome exato do arquivo em `imagens/`. |
| Texto `title: ...` aparece na edição, às vezes no fim da seção anterior. | Frontmatter YAML. | Remova o bloco `---`. |
| Link para outro capítulo não abre no leitor. | Link para o arquivo em vez da âncora. | Troque por `(#id-do-titulo)`. |
| `Duplicate note reference` | A mesma definição de nota (`[^1]:`) em dois capítulos. | Prefixe os rótulos com o capítulo. |
| Lista ou tabela sai como parágrafo corrido. | Falta linha em branco antes do bloco. | Separe o bloco com uma linha vazia. |

## Entrega

- `CHAPTER.md` completo, com título, abertura, desenvolvimento, resultado e fechamento.
- Imagens referenciadas presentes em `imagens/` (preparadas pela etapa 05 quando houver).
- `notas/fontes.md` atualizado com o que mudou durante a reprodução.
- Build sem aviso e um trecho conferido no formato de saída.
- Um resumo para a pessoa: o que foi escrito, o que foi reproduzido e o que ficou pendente.

## Checklist da entrega

- [ ] O arquivo tem um único título `#`, e ele descreve o que o leitor faz.
- [ ] A abertura parte do que o capítulo anterior entregou.
- [ ] Todo termo novo é explicado no primeiro uso.
- [ ] Cada exemplo diz onde executar, o que executar e o que deve aparecer.
- [ ] Todos os exemplos foram executados na ordem do texto e funcionaram.
- [ ] Toda afirmação verificável tem entrada em `notas/fontes.md`.
- [ ] Nomes que aparecem em figuras também aparecem no texto.
- [ ] Links entre capítulos usam âncoras; nenhum link aponta para `CHAPTER.md`.
- [ ] Não há frontmatter YAML nem HTML embutido sem necessidade.
- [ ] O tratamento e o tom seguem o briefing.
- [ ] `ebookfy build` termina sem aviso, e o capítulo foi lido em pelo menos um formato de saída.

## Referências

- [Anatomia do capítulo](references/anatomia-do-capitulo.md): estrutura de um capítulo prático, com um trecho antes e depois da revisão.
- [Markdown do Ebookfy](references/markdown-do-ebookfy.md): recursos aceitos pelo compilador, com exemplos de cada um.

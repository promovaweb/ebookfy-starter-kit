---
name: ebookfy-03-planejar
description: Define a ordem de leitura e transforma as perguntas do leitor em capítulos com resultado observável. Use para criar o primeiro sumário, reorganizar uma edição, dividir ou fundir capítulos. Produz notas/sumario.md, as pastas dos capítulos e as tabelas [[chapters]] na ordem certa.
---

# Planejar o sumário

Esta etapa decide o percurso do leitor. Cada capítulo responde a uma pergunta, parte do que os anteriores já entregaram e termina num resultado que o leitor reconhece. O sumário fica registrado em `notas/sumario.md` e materializado nas pastas e nas tabelas `[[chapters]]` do TOML.

## Quando usar

- Livro novo com briefing pronto e material apurado ou em apuração.
- Edição existente que vai ganhar, perder, dividir ou fundir capítulos.
- Revisão que apontou salto de raciocínio, capítulo repetido ou conceito usado antes de ser apresentado.

Volte à etapa 01 se o briefing não disser quem lê e o que essa pessoa fará ao terminar. Volte à etapa 02 se uma dependência do percurso ainda não tiver fonte. Passe para a etapa 04 com o sumário aprovado.

## Antes de começar

1. Leia `notas/briefing.md`: leitor, ponto de partida, resultado e fora do escopo.
2. Leia `notas/fontes.md` para saber o que já está apurado e o que segue pendente.
3. Rode `ebookfy info` para ver a ordem atual, quando o livro já tiver capítulos.

## Procedimento

1. **Escreva a promessa em uma frase.** "Ao terminar, você terá um fluxo que lê uma planilha toda segunda e envia um resumo por email." Toda escolha do sumário serve a essa frase.
2. **Liste as perguntas do leitor** na ordem natural de quem tenta chegar ao resultado: "Onde instalo?", "Como crio o primeiro fluxo?", "Como agendo?", "Como leio a planilha?", "E se der erro?".
3. **Transforme cada pergunta em capítulo** usando o [roteiro de capítulo](references/roteiro-de-capitulo.md): pergunta, o que o leitor precisa saber antes, o que ele faz no capítulo, o resultado observável, as fontes e o tamanho estimado.
4. **Ordene por dependência.** Um capítulo só usa termos, arquivos e configurações apresentados nos anteriores. Coloque a primeira demonstração completa cedo, de preferência no primeiro ou segundo capítulo, mesmo que simples.
5. **Leia o percurso como o leitor.** Percorra o sumário supondo que só existe o que foi entregue até aquele ponto. Marque onde o leitor travaria. Use os [padrões de sumário](references/padroes-de-sumario.md) para corrigir saltos, repetições e capítulos que só explicam sem levar a uma ação.
6. **Ajuste o tamanho.** Capítulos com resultados independentes podem ser divididos. Dois capítulos que entregam o mesmo resultado viram um.
7. **Escreva os títulos.** O título `#` de cada `CHAPTER.md` aparece no sumário dos três formatos. Prefira títulos que digam o que o leitor faz ("Agendar a primeira execução") a rótulos genéricos ("Agendamento").
8. **Materialize.** Crie `capitulos/NN-slug/CHAPTER.md` com o título e um parágrafo de intenção, e a pasta `imagens/` quando o capítulo tiver figuras. Acrescente uma tabela `[[chapters]]` por capítulo, na ordem decidida.
9. **Confira pelo CLI.** `ebookfy info` lista os títulos na ordem. Leia a lista em voz alta: ela deve contar o percurso sem precisar do resto do livro.
10. **Registre e apresente.** Grave o sumário em `notas/sumario.md` e apresente à pessoa a lista de títulos, a dependência entre capítulos e o que ainda falta apurar. Aguarde a aprovação antes de redigir capítulos inteiros.

## Regras do Ebookfy que afetam esta etapa

- A ordem de leitura vem só das tabelas `[[chapters]]`. O número da pasta é organização, não ordem.
- Prefácio, créditos e autoria vêm de `[files]` e ficam fora da lista: o prefácio abre a edição, créditos e autoria fecham. Introdução e conclusão, quando existirem como unidades próprias, são capítulos comuns no começo e no fim da lista.
- O título do capítulo é o primeiro `#` do arquivo. Use um só `#` por capítulo; subtítulos começam em `##`.
- O mesmo `CHAPTER.md` não pode aparecer duas vezes na lista.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| O capítulo 3 usa um termo explicado no 5. | Ordem por tema, não por dependência. | Traga a explicação para antes do uso ou inverta os capítulos. |
| Três capítulos seguidos só explicam conceitos. | Percurso teórico sem ação. | Junte os conceitos ao capítulo que os usa ou adicione uma demonstração. |
| Dois capítulos chegam ao mesmo resultado. | Divisão por formato, não por tarefa. | Funda os dois ou dê a cada um um resultado próprio. |
| O sumário tem 25 capítulos curtos. | Cada seção virou capítulo. | Agrupe por resultado; seções viram `##` dentro do capítulo. |
| Títulos iguais aos de um índice técnico. | Títulos de rótulo. | Reescreva dizendo o que o leitor faz ou descobre. |

## Entrega

- `notas/sumario.md` com promessa, roteiro por capítulo e mapa de dependências.
- Pastas `capitulos/NN-slug/` com `CHAPTER.md` contendo título e intenção.
- Tabelas `[[chapters]]` na ordem aprovada, conferidas por `ebookfy info`.
- Lista de lacunas que voltam para a etapa 02.

## Checklist da entrega

- [ ] A promessa do livro está escrita em uma frase e todos os capítulos contribuem para ela.
- [ ] Cada capítulo tem pergunta, pré-requisitos, ação do leitor e resultado observável no roteiro.
- [ ] Nenhum capítulo usa termo, arquivo ou configuração apresentado só depois.
- [ ] A primeira demonstração completa aparece até o segundo capítulo.
- [ ] Não há dois capítulos com o mesmo resultado.
- [ ] Cada `CHAPTER.md` tem um único título `#` que descreve o que o leitor faz.
- [ ] `ebookfy info` lista os capítulos na ordem do roteiro.
- [ ] Introdução e conclusão, quando existirem, estão no começo e no fim de `[[chapters]]`.
- [ ] As lacunas de fonte estão listadas para a etapa 02.
- [ ] A pessoa aprovou o sumário antes da redação dos capítulos.

## Referências

- [Roteiro de capítulo](references/roteiro-de-capitulo.md): campos do roteiro e um sumário completo de exemplo.
- [Padrões de sumário](references/padroes-de-sumario.md): estruturas comuns por tipo de livro e como corrigir percursos com problema.

---
name: ebookfy-08-prefacio
description: Redige ou revisa o prefácio apontado por files.preface. Use para apresentar a obra antes dos capítulos (para quem foi feita, de onde veio, o que o leitor terá ao terminar e como percorrer o livro), ou para corrigir um prefácio genérico, longo ou que promete o que o livro não entrega.
---

# Redigir o prefácio

O prefácio é a primeira coisa que o leitor encontra depois da capa e do sumário. Ele responde, em pouco espaço, se este livro é para ele e como aproveitá-lo. Não ensina nada ainda: essa é a função da introdução e dos capítulos.

## Quando usar

- Livro novo, de preferência depois que o sumário estiver estável. Um rascunho no início ajuda a fixar a promessa; a versão final vem depois da revisão.
- O sumário mudou e o prefácio ainda descreve o percurso antigo.
- A revisão apontou prefácio genérico, longo ou com promessa sem capítulo correspondente.

Use a etapa 07 para a introdução e a etapa 10 para a apresentação de autoria.

## Antes de começar

1. Leia `notas/briefing.md`: leitor, ponto de partida, resultado, fora do escopo.
2. Leia a lista de títulos com `ebookfy info` e o roteiro em `notas/sumario.md`.
3. Leia o último capítulo: o prefácio promete o que ele entrega.
4. Confirme quem assina o prefácio. Pode ser a autoria, a editora ou uma pessoa convidada.

## Procedimento

1. **Defina quem fala.** Prefácio assinado pela autoria fala em primeira pessoa; prefácio institucional fala pela editora; prefácio convidado fala de quem convida. Registre a escolha e mantenha até o fim.
2. **Responda às quatro perguntas** do [roteiro do prefácio](references/roteiro-do-prefacio.md): para quem é, de onde veio, o que o leitor terá ao terminar, como ler.
3. **Seja específico sobre o leitor.** "Para quem cuida de um pequeno negócio e repete tarefas em planilhas" funciona; "para todos que se interessam por tecnologia" não filtra ninguém.
4. **Conte a origem com fatos confirmados.** Turma, projeto, pesquisa ou problema real que deu origem ao livro. Relatos pessoais só com confirmação de quem os viveu. Nada de experiência inventada para dar calor ao texto.
5. **Indique percursos**, quando houver públicos diferentes: "Se você já tem o n8n instalado, comece pelo capítulo *Montar o primeiro fluxo*". Cite o capítulo pelo título, que é o que aparece no sumário.
6. **Agradeça com moderação**, se for o caso. Uma ou duas frases; lista longa vai para os créditos.
7. **Confira cada promessa.** Para cada coisa que o prefácio diz que o leitor vai aprender ou ter, aponte o capítulo que entrega. Promessa sem capítulo sai do texto.
8. **Mantenha curto.** Uma a duas páginas no PDF. Leia em voz alta: o que soa como discurso, corte.

## Regras do Ebookfy que afetam esta etapa

- O caminho vem de `files.preface`, normalmente `editorial/prefacio.md`. O arquivo precisa existir e começar com um título `#`.
- O prefácio é o primeiro texto da edição, antes de todos os capítulos, e aparece no sumário com o seu título.
- Use o título "Prefácio" ou outro que a obra pedir ("Antes de começar", "Por que este livro"). Ele aparece no sumário dos três formatos.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| Prefácio de quatro páginas. | Introdução e histórico misturados ao prefácio. | Mova o conteúdo de trabalho para a introdução; corte o histórico. |
| "Este livro vai transformar sua forma de trabalhar." | Promessa grandiosa sem lastro. | Troque pelo resultado concreto do último capítulo. |
| Cita um capítulo que não existe mais. | Sumário mudou depois do prefácio. | Releia com `ebookfy info` e atualize os títulos citados. |
| Relato pessoal que ninguém confirmou. | Texto criado para parecer próximo. | Remova ou peça confirmação à pessoa citada. |
| Lista de vinte agradecimentos. | Créditos dentro do prefácio. | Mova para `files.credits`. |

## Entrega

- `editorial/prefacio.md` (ou o arquivo de `files.preface`) com título e texto final.
- Cada promessa do prefácio ligada a um capítulo, conferida na resposta à pessoa.
- Pendências de confirmação de relatos, quando houver.

## Checklist da entrega

- [ ] O arquivo apontado por `files.preface` existe e começa com um título `#`.
- [ ] Quem fala no prefácio está definido e se mantém do início ao fim.
- [ ] O leitor está descrito de forma específica, com situação e ponto de partida.
- [ ] A origem da obra usa apenas fatos confirmados.
- [ ] Cada promessa do prefácio corresponde a um capítulo existente.
- [ ] Capítulos citados aparecem pelo título atual do sumário.
- [ ] Não há procedimento nem ensino de conteúdo; isso fica para a introdução e os capítulos.
- [ ] O texto ocupa no máximo duas páginas no PDF.
- [ ] Agradecimentos longos foram para os créditos.

## Referências

- [Roteiro do prefácio](references/roteiro-do-prefacio.md): as quatro perguntas, um exemplo completo e frases a evitar.

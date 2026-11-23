# Modelo de briefing

Grave em `notas/briefing.md`. Cada resposta deve caber em uma ou duas frases concretas. Quando a pessoa não souber responder, escreva `Pendente:` seguido do que falta e de quem pode responder.

## Perguntas

1. **Leitor.** Quem vai ler? Descreva a ocupação ou situação, não uma faixa demográfica.
2. **Ponto de partida.** O que essa pessoa já sabe fazer e o que ela tem em mãos ao abrir o livro?
3. **Resultado.** O que ela conseguirá fazer ou entender ao terminar? Prefira algo observável.
4. **Fora do escopo.** O que o livro não vai cobrir, mesmo que pareça relacionado?
5. **Tom.** Como o texto fala com o leitor: tratamento (você, tu, impessoal), grau de formalidade, uso de termos técnicos.
6. **Fontes disponíveis.** Que material já existe: rascunhos, aulas, transcrições, documentação, entrevistas.
7. **Assinatura.** Quem assina, com que grafia, e quem aprova título, capa e textos de autoria.
8. **Edição.** Formatos de entrega, prazo, canal de distribuição e condição de acesso (público, alunos, clientes).
9. **Identificação.** `slug`, `identifier` e versão inicial escolhidos para a obra.

## Pendências por etapa

Feche o briefing com três listas: afirmações que precisam de fonte (etapa 02), capítulos que ainda não têm material (etapa 03) e materiais de terceiros sem autorização registrada (etapa 09).

## Exemplo preenchido

```markdown
# Briefing · Primeiros fluxos no n8n

- Leitor: dono ou funcionário de pequeno negócio que repete tarefas em planilhas e email todos os dias.
- Ponto de partida: usa planilhas e email com segurança, nunca instalou um servidor, tem um computador com Docker ou uma conta na nuvem do n8n.
- Resultado: um fluxo que lê uma planilha toda segunda-feira e envia um resumo por email, rodando sem intervenção.
- Fora do escopo: filas, modo de alta disponibilidade, código JavaScript avançado.
- Tom: "você", frases curtas, termos do n8n em inglês como aparecem na interface (Trigger, Node, Workflow).
- Fontes: gravação de três aulas ao vivo (notas/aulas/), documentação oficial do n8n 2.x, prints da instância de testes.
- Assinatura: "Ana Souza". Ana aprova título e autoria; a capa passa por Marcos.
- Edição: PDF e EPUB, alunos da turma de março, link privado na área do aluno.
- Identificação: slug primeiros-fluxos-n8n, identifier urn:editora-exemplo:primeiros-fluxos-n8n, versão 1.0.0.

## Pendências

- Etapa 02: confirmar se o Schedule Trigger mantém o fuso da instância ou do usuário na versão atual.
- Etapa 03: falta material para o capítulo de tratamento de erros.
- Etapa 09: o diagrama da aula 2 veio de um slide de terceiro; pedir autorização ou redesenhar.
```

## Sinais de briefing fraco

- O resultado diz "entender melhor" ou "dominar" sem dizer o que a pessoa fará.
- Leitor e ponto de partida descrevem pessoas diferentes.
- O tom não define o tratamento, e cada capítulo acaba usando um.
- Não há ninguém nomeado para aprovar título e autoria.

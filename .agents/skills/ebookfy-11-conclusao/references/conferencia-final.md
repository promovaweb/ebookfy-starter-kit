# Conferência final

> Os exemplos usam um livro fictício, *Primeiros fluxos no n8n*.

## Modelo

Cada item da conferência tem três partes: o que verificar, como verificar e onde voltar se falhar.

| Verifique | Como | Se falhar, volte a |
| --- | --- | --- |
| O fluxo está ativo. | A chave no topo do editor mostra **Active**. | *Agendar a execução* |
| Ele rodou no último horário agendado. | A aba **Executions** mostra uma execução *Succeeded* na última segunda às 9h. | *Agendar a execução*, seção sobre fuso horário |
| O email chegou com os totais certos. | Compare o total do email com a soma na planilha. | *Ler uma planilha* |
| Você recebe alerta quando ele falha. | Renomeie a aba da planilha, execute e confira o alerta. Desfaça a mudança. | *Receber um alerta quando o fluxo falhar* |

## Exemplo de encerramento

```markdown
## O que você tem agora

Você tem um fluxo que roda sozinho toda segunda-feira às 9h, lê a planilha de vendas, calcula
os totais e envia o relatório por email. Quando algo dá errado, um alerta chega antes de o
sócio perguntar pelo relatório.

Antes de deixar o fluxo trabalhando sozinho, percorra a conferência:

| Verifique | Como | Se falhar, volte a |
| --- | --- | --- |
| ... | ... | ... |

## Próximos passos

O mesmo fluxo resolve outras rotinas com poucas mudanças. Troque a planilha de vendas pela de
contas a pagar e envie o resumo na sexta, ou duplique o fluxo e mude o destinatário para a
equipe de compras. Os dois casos usam apenas os nodes que você já conhece.

Quando quiser ir além, a [documentação do n8n](https://docs.n8n.io/) descreve todos os nodes
disponíveis, e o fórum da comunidade reúne fluxos prontos para adaptar.

Na próxima segunda, compare o tempo que você gastava montando o relatório com o tempo que
gasta agora conferindo o email. O próximo fluxo vai ser mais rápido de montar.
```

## Teste com duas amostras

Percorra a conferência com:

1. **Uma amostra pronta**: o projeto final, montado seguindo o livro.
2. **Uma amostra incompleta**: o mesmo projeto com uma falha típica (fluxo inativo, fuso errado, aba renomeada).

A amostra pronta passa em todos os itens; a incompleta falha em pelo menos um, e o item aponta o capítulo certo. Se as duas passam, a conferência está vaga.

## Frases a evitar

| Evite | No lugar |
| --- | --- |
| "Chegamos ao fim da nossa jornada." | O que o leitor tem agora. |
| "Neste livro vimos X, Y e Z." | Conferência do resultado. |
| "Agora o céu é o limite." | Uma variação concreta que ele consegue fazer. |
| "Espero ter contribuído para seu crescimento." | Termine no trabalho do leitor. |

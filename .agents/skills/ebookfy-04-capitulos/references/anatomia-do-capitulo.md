# Anatomia do capítulo

> Os exemplos usam um livro fictício, *Primeiros fluxos no n8n*. Nomes de botões e mensagens ilustram a estrutura.

## Estrutura de um capítulo prático

| Parte | Função | Tamanho típico |
| --- | --- | --- |
| Título | Diz o que o leitor faz. | Uma linha. |
| Abertura | Situa o leitor: o que ele tem do capítulo anterior e o que terá ao fim. | Um parágrafo. |
| Preparação | O que precisa estar aberto, instalado ou disponível. | Um parágrafo ou lista curta. |
| Execução | Os passos, com o resultado de cada passo importante. | A maior parte do capítulo. |
| Resultado | Como reconhecer que deu certo. | Um parágrafo, às vezes com figura. |
| Variação ou erro comum | O desvio mais provável e como sair dele. | Uma seção curta. |
| Fechamento | O que o leitor tem agora e onde isso será usado. | Um parágrafo. |

Capítulos de conceito seguem a mesma lógica: em vez de passos, um caso concreto que mostra o conceito funcionando, e o resultado é o leitor conseguir reconhecer o conceito num caso novo.

Capítulos narrativos trocam a execução por cena, acontecimento e interpretação. A abertura ainda situa o leitor no tempo e no lugar, e o fechamento ainda diz o que mudou.

## Antes e depois

### Antes

```markdown
# Agendamento

O agendamento é uma das funcionalidades mais importantes do n8n. Com ele, é possível
automatizar diversos processos. Para agendar, basta usar o Schedule Trigger e configurar
o horário desejado. Depois é só ativar o workflow.
```

Problemas: título de rótulo; abertura genérica que não diz onde o leitor está; "basta" esconde passos; não diz onde clicar nem como saber que funcionou; "diversos processos" não informa nada.

### Depois

````markdown
# Agendar a execução

No capítulo anterior, você executou o fluxo clicando em **Execute workflow**. Agora ele vai
rodar sozinho toda segunda-feira às 9h, sem você abrir o editor.

## Trocar o gatilho

Abra o fluxo do capítulo anterior. Clique no node **Manual Trigger** e apague-o com a tecla
Delete. No lugar dele, clique em **Add first step**, procure por *Schedule* e escolha
**Schedule Trigger**.

![Painel do Schedule Trigger com o intervalo semanal selecionado](imagens/schedule-semanal.png)

No painel, defina **Trigger Interval** como *Weeks*, marque *Monday* e escolha 9 em
**Trigger at Hour**. Ligue a saída do Schedule Trigger à entrada do node **Set**.

## Ativar e conferir

Um fluxo agendado só roda quando está ativo. Clique na chave **Inactive** no topo do editor;
ela muda para **Active**.

Para conferir sem esperar até segunda, mude temporariamente o intervalo para *Minutes* com
valor 1. Em até um minuto, a aba **Executions** mostra uma execução com status *Succeeded*.
Volte o intervalo para semanal depois do teste.

## Se a execução sair no horário errado

O Schedule Trigger usa o fuso horário do workflow ou, sem ele, o da instância. Se a execução
apareceu três horas adiantada, abra **Settings** do workflow e escolha *America/Sao_Paulo*
em **Timezone**.

Agora o fluxo roda sozinho. No próximo capítulo, ele passa a ler uma planilha a cada
execução, em vez de criar dados fixos no Set.
````

O que mudou: título diz a ação; abertura parte do capítulo anterior; cada passo diz onde clicar; a figura tem legenda que diz o que observar; há uma forma de conferir sem esperar uma semana; o erro mais provável tem saída; o fechamento aponta para o próximo capítulo.

## Leitura de iniciante

Antes de entregar, releia procurando:

| Marca no texto | Pergunta a fazer |
| --- | --- |
| "basta", "simplesmente", "é só" | Que passos essas palavras escondem? |
| Nome de botão só na figura | O texto também diz o nome? |
| "Configure conforme necessário" | Qual valor o leitor deve usar neste exemplo? |
| Comando sem pasta | De onde o leitor executa? |
| Resultado sem descrição | O que aparece na tela quando dá certo? |
| Termo novo sem explicação | O leitor já viu isso num capítulo anterior? |

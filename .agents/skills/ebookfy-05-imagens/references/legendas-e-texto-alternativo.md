# Legendas e texto alternativo

> Os exemplos usam um livro fictício, *Primeiros fluxos no n8n*.

No Ebookfy, o texto entre colchetes de uma figura cumpre duas funções ao mesmo tempo: é a legenda impressa embaixo da imagem e o texto alternativo lido por leitores de tela. Escreva pensando nas duas.

## Como escrever

1. Comece pelo que o leitor deve observar, não pelo tipo de imagem.
2. Cite os nomes que aparecem na tela e que o texto usa.
3. Inclua o valor ou o estado mostrado quando ele importa para o passo.
4. Mantenha em uma frase. Detalhes vão para o parágrafo.
5. Não comece com "Imagem de", "Captura de tela de" ou "Figura mostrando".

## Exemplos

| Fraca | Melhor | Por quê |
| --- | --- | --- |
| `![](imagens/img1.png)` | `![Painel do Schedule Trigger com o intervalo semanal e a hora 9](imagens/schedule-semanal.png)` | A legenda vazia não orienta o leitor nem o leitor de tela. |
| `![schedule-semanal.png](...)` | `![Schedule Trigger configurado para segunda-feira às 9h](...)` | O nome do arquivo não descreve nada. |
| `![Captura de tela do n8n](...)` | `![Aba Executions com uma execução Succeeded às 09:00](...)` | "Captura de tela" ocupa espaço sem informar. |
| `![Tela](...)` | `![Chave Active ligada no topo do editor](...)` | Diz qual elemento procurar. |
| `![Diagrama](...)` | `![Fluxo em três etapas: agenda, lê a planilha, envia o email](...)` | Descreve a estrutura do diagrama. |
| `![Foto da equipe reunida numa sala com computadores e uma janela ao fundo num dia de sol](...)` | `![Equipe do suporte durante o primeiro teste do fluxo](...)` | Descrição visual exaustiva não ajuda; diga por que a foto está ali. |

## Legenda e parágrafo trabalham juntos

A figura não substitui o texto. O parágrafo diz o que fazer e a figura confirma onde.

````markdown
No painel, defina **Trigger Interval** como *Weeks*, marque *Monday* e escolha 9 em
**Trigger at Hour**.

![Painel do Schedule Trigger com o intervalo semanal, segunda-feira marcada e hora 9](imagens/schedule-semanal.png)
````

Quem não vê a imagem consegue seguir o passo pelo parágrafo. Quem vê a imagem confirma que preencheu igual.

## Figuras decorativas

Ebooks técnicos raramente precisam de imagem decorativa. Se houver uma (abertura de parte, ilustração de capítulo), a legenda pode ser curta e descritiva: `![Ilustração de um livro aberto com marcador](imagens/abertura.png)`. Ela ainda aparecerá impressa, então evite deixar vazia.

## Figura dentro de lista numerada

Para colocar uma figura entre dois passos de uma lista, indente a imagem com quatro espaços e deixe linhas em branco em volta, para que ela pertença ao passo anterior e a numeração continue.

````markdown
1. Clique em **Add first step**.

    ![Busca de nodes com Schedule digitado](imagens/busca-schedule.png)

2. Escolha **Schedule Trigger**.
````

# Roteiro da abertura

> Os exemplos usam um livro fictício, *Primeiros fluxos no n8n*.

## Um parágrafo, uma função

| Parágrafo | Pergunta que responde |
| --- | --- |
| 1. Situação | Onde o leitor está hoje e o que o incomoda? |
| 2. Destino | O que ele terá ao fim do livro? |
| 3. Requisitos | O que precisa ter em mãos antes de começar? |
| 4. Convenções | Como ler os exemplos do livro? (opcional) |
| 5. Primeira ação | O que ele faz agora? |

## Versão fraca

```markdown
# Introdução

A automação de processos é uma tendência crescente no mundo dos negócios. Desde a Revolução
Industrial, a humanidade busca formas de automatizar tarefas repetitivas. Hoje, com o avanço
da tecnologia, ferramentas como o n8n permitem que qualquer pessoa crie automações poderosas.

Este livro foi escrito para ajudar você a dar os primeiros passos nesse universo fascinante.
Ao longo dos capítulos, vamos explorar diversos conceitos e funcionalidades.

Boa leitura!
```

Problemas: começa pela história do assunto; "tendência crescente", "universo fascinante" e "diversos conceitos" não dizem nada; não diz o que o leitor vai construir nem do que precisa; termina sem ação.

## Versão de trabalho (abertura do primeiro capítulo)

````markdown
# Instalar o n8n e abrir o editor

Toda segunda-feira você abre a planilha de vendas, copia os totais da semana e manda um email
para o sócio. Leva vinte minutos e, quando você viaja, não acontece.

Ao fim deste livro, um fluxo no n8n fará isso sozinho: às 9h de segunda ele lê a planilha,
calcula os totais e envia o email, e avisa você se algo der errado.

Para acompanhar, você precisa de:

- um computador com Docker instalado, ou uma conta gratuita no n8n Cloud;
- uma conta Google com acesso a uma planilha (o capítulo 4 traz um modelo para copiar);
- uma conta de email que aceite envio por SMTP.

Os comandos aparecem em blocos de código e rodam na pasta `n8n-livro`, que você vai criar
agora. Os arquivos de exemplo de cada capítulo estão no repositório indicado no prefácio.

## Criar a pasta do projeto

Abra o terminal e crie a pasta onde o n8n vai guardar os dados:

```bash
mkdir n8n-livro
cd n8n-livro
```
````

O que funciona: começa na rotina do leitor; o destino é concreto e verificável; requisitos estão todos antes do primeiro uso, inclusive o que só será usado no capítulo 4; convenções em uma frase; o primeiro `##` já é uma ação.

## Conferência

Antes de entregar, leia a abertura e responda:

- O leitor sabe, em uma frase, o que vai construir?
- Existe algum requisito que só aparece depois do primeiro capítulo?
- Alguma frase poderia estar em qualquer livro sobre qualquer assunto? Corte.
- A primeira ação funciona com o que foi dito até ali?
- Algo aqui repete o prefácio?

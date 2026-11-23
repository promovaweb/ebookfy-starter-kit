# Roteiro de capítulo

> Os exemplos usam um livro fictício, *Primeiros fluxos no n8n*. Títulos e conteúdos ilustram o formato do roteiro.

Grave em `notas/sumario.md`. O arquivo começa pela promessa do livro e segue com um bloco por capítulo, na ordem de leitura.

## Campos de cada capítulo

| Campo | Pergunta que responde |
| --- | --- |
| Título | Que frase aparece no sumário? |
| Pasta | Qual pasta em `capitulos/`? |
| Pergunta do leitor | O que o leitor quer saber ao chegar aqui? |
| Pré-requisitos | Que termos, arquivos e configurações ele já precisa ter, e de qual capítulo vieram? |
| O que o leitor faz | Qual a ação principal do capítulo? |
| Resultado observável | Como o leitor sabe que conseguiu? |
| Fontes | Quais entradas de `notas/fontes.md` sustentam o capítulo? |
| Figuras previstas | Que imagens o leitor precisa ver? |
| Tamanho | Estimativa em páginas ou palavras. |
| Pendências | O que falta apurar ou decidir? |

## Exemplo de sumário

O exemplo mostra os três primeiros roteiros completos; os capítulos 04 a 07 aparecem só com o título, mas no arquivo real cada um tem todos os campos.

```markdown
# Sumário · Primeiros fluxos no n8n

Promessa: ao terminar, você terá um fluxo que lê uma planilha toda segunda-feira e envia um resumo por email, rodando sem intervenção.

## 01 · Instalar o n8n e abrir o editor
- Pasta: capitulos/01-instalar/
- Pergunta: onde e como coloco o n8n para rodar?
- Pré-requisitos: computador com Docker ou conta na nuvem (briefing).
- O leitor faz: sobe o n8n com Docker Compose ou cria a conta na nuvem.
- Resultado: o editor abre no navegador e mostra um workflow vazio.
- Fontes: F-01-01 a F-01-04.
- Pendências: F-01-05 (limite de execuções do plano na nuvem).
- Figuras: editor vazio com a barra lateral.
- Tamanho: 8 páginas.

## 02 · Montar o primeiro fluxo
- Pasta: capitulos/02-primeiro-fluxo/
- Pergunta: como um fluxo funciona na prática?
- Pré-requisitos: editor aberto (cap. 01).
- O leitor faz: liga um Manual Trigger a um node Set e executa.
- Resultado: o painel de saída mostra o item criado pelo Set.
- Fontes: F-02-01, F-02-02.
- Figuras: canvas com os dois nodes; painel de saída.
- Tamanho: 10 páginas.

## 03 · Agendar a execução
- Pasta: capitulos/03-agendar/
- Pergunta: como faço o fluxo rodar sozinho?
- Pré-requisitos: fluxo do cap. 02.
- O leitor faz: troca o Manual Trigger pelo Schedule Trigger e ativa o fluxo.
- Resultado: o histórico de execuções mostra uma execução no horário agendado.
- Fontes: F-03-01 (fuso horário do agendamento).
- Figuras: painel do Schedule Trigger com intervalo semanal; aba Executions.
- Tamanho: 6 páginas.

## 04 · Ler uma planilha
## 05 · Enviar o resumo por email
## 06 · Tratar erros e receber alertas
## 07 · Colocar o fluxo em produção
```

## Mapa de dependências

Feche o sumário com uma linha por capítulo dizendo de quais anteriores ele depende. O mapa mostra rapidamente um capítulo que depende de outro posterior.

```markdown
## Dependências
- 02 depende de 01
- 03 depende de 02
- 04 depende de 02
- 05 depende de 04
- 06 depende de 03 e 05
- 07 depende de 06
```

## Do roteiro para o TOML

```toml
[[chapters]]
file = "capitulos/01-instalar/CHAPTER.md"

[[chapters]]
file = "capitulos/02-primeiro-fluxo/CHAPTER.md"

[[chapters]]
file = "capitulos/03-agendar/CHAPTER.md"
```

E o esqueleto de cada `CHAPTER.md`, que a etapa 04 vai expandir:

```markdown
# Agendar a execução

Neste capítulo, o fluxo do capítulo anterior passa a rodar sozinho toda segunda-feira às 9h.
```

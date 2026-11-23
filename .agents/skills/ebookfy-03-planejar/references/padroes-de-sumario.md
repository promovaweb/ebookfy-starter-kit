# Padrões de sumário

## Estruturas por tipo de livro

| Tipo de livro | Estrutura que costuma funcionar | Cuidado |
| --- | --- | --- |
| Guia prático | Primeiro resultado simples, depois uma capacidade por capítulo, no fim o projeto completo. | Não abrir com três capítulos de conceitos. |
| Manual de referência | Primeiros passos, depois um capítulo por área (configuração, comandos, erros) e um apêndice de referência. | Cada área ainda precisa de um exemplo; tabela sozinha não ensina. |
| Livro de método | Problema, princípios, aplicação passo a passo, casos, armadilhas. | Princípios só fazem sentido depois do leitor ver o problema. |
| Relato ou narrativa | Ordem dos acontecimentos ou ordem das descobertas, com interpretação ao fim de cada parte. | Saltos no tempo precisam de marcação clara no título ou na abertura. |
| Coletânea | Agrupamento por tema, com um texto de abertura que explique o recorte. | A ordem dentro de cada grupo também precisa de motivo. |

## Problemas de percurso e como corrigir

### Salto de dependência

Sintoma: o capítulo 4 diz "use a credencial que você criou" e ninguém criou credencial antes.

Correção: localize o primeiro uso de cada termo, arquivo ou configuração. Se o primeiro uso vem antes da apresentação, mova a apresentação para o capítulo do uso ou para um anterior.

### Teoria em bloco

Sintoma: capítulos 1 a 3 explicam o que é automação, o que é um node e o que é um gatilho, e só o 4 tem uma ação.

Correção: comece pela ação mais simples que já produz resultado e apresente cada conceito no capítulo que o usa. O leitor guarda melhor um conceito quando acabou de precisar dele.

### Resultado repetido

Sintoma: "Criar um fluxo" e "Seu primeiro workflow" terminam com o mesmo fluxo de dois nodes.

Correção: funda os dois ou dê ao segundo um resultado novo (por exemplo, o mesmo fluxo agora agendado).

### Capítulo sem resultado

Sintoma: o roteiro não consegue preencher "resultado observável".

Correção: pergunte o que o leitor consegue fazer depois do capítulo que não conseguia antes. Se a resposta for "nada", o conteúdo é apoio e cabe dentro de outro capítulo, ou num apêndice no fim da lista.

### Capítulo grande demais

Sintoma: um capítulo com 40 páginas e quatro resultados diferentes.

Correção: divida por resultado. Cada parte ganha pasta, título e tabela própria.

## Títulos

| Rótulo genérico | Título que diz o que acontece |
| --- | --- |
| Agendamento | Agendar a primeira execução |
| Tratamento de erros | Receber um alerta quando o fluxo falhar |
| Conclusão | Colocar o fluxo em produção e acompanhar |
| Introdução | O que você vai construir neste livro |

O título aparece no sumário do PDF, na navegação do EPUB e na TUI do Ebookfy. Leia a lista de títulos sozinha: ela deve contar o percurso do livro.

## Introdução e conclusão

O Ebookfy não tem campo próprio para introdução ou conclusão. Use um capítulo comum:

- Introdução curta: abra o primeiro capítulo com ela (etapa 07).
- Introdução longa: crie `capitulos/00-introducao/CHAPTER.md` e coloque a tabela no início da lista.
- Conclusão: feche o último capítulo com ela ou crie um capítulo final antes dos créditos (etapa 11).

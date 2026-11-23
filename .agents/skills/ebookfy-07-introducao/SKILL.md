---
name: ebookfy-07-introducao
description: Escreve a abertura do livro, seja no início do primeiro capítulo ou como capítulo de introdução próprio. Use para levar o leitor da situação inicial à primeira ação com o que ele já tem em mãos, ou para corrigir uma introdução longa, genérica ou que repete o prefácio.
---

# Preparar a introdução

A introdução é a primeira página de trabalho do livro. Ela recebe o leitor que acabou de sair do prefácio, mostra o que ele vai construir ao longo da obra e o coloca na primeira ação o quanto antes. Prefácio e introdução têm funções diferentes: o prefácio apresenta a obra; a introdução começa o percurso.

## Quando usar

- Livro novo, depois do sumário aprovado e antes ou junto da redação do primeiro capítulo.
- A revisão apontou que o leitor leva páginas demais para fazer a primeira coisa.
- A abertura repete o prefácio ou faz histórico do assunto antes de qualquer ação.

Use a etapa 08 para o prefácio e a 04 para o restante do primeiro capítulo.

## Antes de começar

1. Leia o prefácio (`files.preface`) inteiro, em especial o último parágrafo.
2. Leia o roteiro dos dois primeiros capítulos em `notas/sumario.md`.
3. Releia o ponto de partida do leitor e a promessa em `notas/briefing.md`.

## Escolha o formato

| Situação | Formato | Onde |
| --- | --- | --- |
| A introdução cabe em três ou quatro parágrafos e leva direto ao primeiro passo. | Abertura do primeiro capítulo. | Início do primeiro `CHAPTER.md`, antes do primeiro `##`. |
| O leitor precisa de um panorama do projeto completo, requisitos e convenções antes de começar. | Capítulo de introdução. | `capitulos/00-introducao/CHAPTER.md`, primeira tabela de `[[chapters]]`. |

Na dúvida, prefira a abertura curta. Um capítulo de introdução precisa ter resultado próprio, como o ambiente preparado ou o leitor sabendo exatamente o que vai construir.

## Procedimento

1. **Comece onde o leitor está.** Primeira frase sobre a situação dele, não sobre o assunto: "Toda segunda você abre a planilha de vendas, copia os números e manda um email para o sócio."
2. **Mostre o destino.** Descreva em um parágrafo o que ele terá ao fim do livro, de preferência com uma imagem ou exemplo do resultado final.
3. **Liste o que precisa ter em mãos.** Requisitos concretos: programa, versão, conta, arquivo de exemplo. Se algo exige preparo (instalar, pedir acesso), diga isso aqui, não no meio do capítulo 3.
4. **Combine as convenções**, se houver: como o livro mostra comandos, o que significa um bloco destacado, onde estão os arquivos de exemplo. Uma lista curta basta.
5. **Leve à primeira ação.** Termine com o leitor fazendo algo: abrir o programa, baixar o arquivo de exemplo, rodar o primeiro comando. No formato de abertura, essa ação é o primeiro `##` do capítulo.
6. **Corte o que já está no prefácio.** Público, origem da obra e agradecimentos ficam no prefácio. Use o [roteiro da abertura](references/roteiro-da-abertura.md) para conferir cada parágrafo.
7. **Teste a primeira ação.** Execute o primeiro passo usando só as informações dadas até ali. Se faltou algo (uma conta, um arquivo, uma permissão), acrescente no ponto de uso.

## Regras do Ebookfy que afetam esta etapa

- O prefácio é lido logo antes do primeiro capítulo. A introdução não precisa repetir o que ele acabou de dizer.
- Um capítulo de introdução é um capítulo comum: pasta própria, `CHAPTER.md`, um título `#` e uma tabela no início de `[[chapters]]`.
- O título da introdução aparece no sumário. "Introdução" funciona, mas um título que diga o que o leitor vai construir orienta mais.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| Duas páginas antes da primeira ação. | Histórico e contexto demais. | Corte o histórico; deixe só o necessário para agir. |
| Introdução repete o prefácio. | Fronteira entre os dois não definida. | Prefácio apresenta a obra; introdução começa o trabalho. Corte a repetição. |
| Requisito aparece no capítulo 3 ("você vai precisar de uma conta X"). | Requisitos não listados na abertura. | Traga para a lista de requisitos da introdução. |
| Abertura promete o que o livro não entrega. | Promessa escrita antes do sumário final. | Compare com o último capítulo e ajuste. |

## Entrega

- Abertura no primeiro `CHAPTER.md` ou capítulo de introdução com tabela no início de `[[chapters]]`.
- Requisitos e convenções do livro listados num só lugar.
- Primeira ação testada com as informações disponíveis até aquele ponto.

## Checklist da entrega

- [ ] A primeira frase fala da situação do leitor, não da história do assunto.
- [ ] O resultado final do livro está descrito de forma concreta.
- [ ] Todos os requisitos (programas, versões, contas, arquivos) aparecem antes do primeiro uso.
- [ ] As convenções do livro, se houver, estão explicadas uma vez.
- [ ] A introdução termina com o leitor fazendo algo.
- [ ] Nada repete o prefácio.
- [ ] A primeira ação foi executada usando só o que o texto informou até ali.
- [ ] Se for capítulo próprio, ele está na primeira tabela de `[[chapters]]` e tem resultado próprio.
- [ ] Se for capítulo próprio, `ebookfy info` mostra a introdução em primeiro lugar; se for abertura do primeiro capítulo, ela aparece antes do primeiro `##` no arquivo e na prova.

## Referências

- [Roteiro da abertura](references/roteiro-da-abertura.md): perguntas de cada parágrafo e um exemplo completo, com a versão fraca ao lado.

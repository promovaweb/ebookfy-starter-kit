---
name: ebookfy-11-conclusao
description: Escreve ou corrige o encerramento do livro, no fim do último capítulo ou como capítulo final próprio. Use para fechar a leitura com o resultado que o leitor construiu, uma forma de conferir se a tarefa ficou pronta e um próximo passo que ele já consegue dar, ou para substituir um encerramento genérico.
---

# Escrever a conclusão

A conclusão fecha o percurso que a introdução abriu. Ela mostra ao leitor o que ele tem nas mãos agora, dá uma forma de conferir se o trabalho está mesmo pronto e aponta um próximo passo possível com o que ele já sabe. Não é um resumo dos capítulos nem um discurso de despedida.

## Quando usar

- Livro com capítulos redigidos, antes da revisão completa.
- A revisão apontou encerramento genérico, resumo dos capítulos ou despedida sem conteúdo.
- O último capítulo mudou e a conclusão ficou desatualizada.

Depois da conclusão, revise o prefácio (etapa 08) se o resultado final mudou. Passe para a etapa 12 com o livro completo.

## Antes de começar

1. Leia a promessa no prefácio e o destino descrito na introdução.
2. Leia o último capítulo inteiro e o resultado de cada capítulo em `notas/sumario.md`.
3. Liste o que o leitor realmente produziu ao longo do livro: arquivos, configurações, um sistema funcionando, uma compreensão que ele aplica.

## Escolha o formato

| Situação | Formato | Onde |
| --- | --- | --- |
| O último capítulo já termina no resultado final. | Seção de encerramento. | Último `##` do último `CHAPTER.md`. |
| O livro precisa de uma conferência completa ou de caminhos para depois. | Capítulo final. | `capitulos/NN-proximos-passos/CHAPTER.md`, última tabela de `[[chapters]]`. |

## Procedimento

1. **Retome o resultado.** Um parágrafo dizendo o que o leitor tem agora, em termos concretos: "Você tem um fluxo que roda toda segunda às 9h, lê a planilha, envia o relatório e avisa quando falha."
2. **Ofereça uma conferência final.** Uma lista curta que o leitor percorre para saber se o trabalho está pronto, como no [modelo de conferência final](references/conferencia-final.md). Cada item deve ser verificável, não uma impressão.
3. **Aponte o retorno.** Para cada item da conferência que pode falhar, indique o capítulo que resolve, pelo título.
4. **Proponha o próximo passo.** Uma ou duas variações que o leitor já consegue fazer com o que aprendeu: outro relatório, outra fonte de dados, outro horário. Evite apontar para assuntos que o livro não preparou.
5. **Indique para onde ir depois**, se fizer sentido: documentação oficial, comunidade, obra seguinte. Com links conferidos.
6. **Termine no leitor.** A última frase fala do trabalho dele, não da jornada do autor nem de agradecimentos.
7. **Teste a conferência** com duas amostras: um projeto pronto e um incompleto. Se as duas passam na conferência, os itens estão vagos demais.
8. **Revise o prefácio** se a conclusão mostrar que o resultado final mudou.

## Regras do Ebookfy que afetam esta etapa

- Depois do último capítulo vêm os créditos e a autoria, de `[files]`. A conclusão é o último texto de conteúdo.
- Um capítulo final é um capítulo comum, com pasta, `CHAPTER.md`, um título `#` e a última tabela de `[[chapters]]`.
- Links para capítulos anteriores usam a âncora do título, nunca o caminho do arquivo.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| Conclusão resume capítulo por capítulo. | Resumo no lugar de fechamento. | Troque por resultado final, conferência e próximo passo. |
| "Agora você está pronto para qualquer desafio." | Promessa vaga. | Diga o que exatamente ele consegue fazer. |
| Próximo passo exige assunto não coberto. | Variação fora do alcance do livro. | Escolha uma variação com os recursos já ensinados. |
| Conferência com itens como "entendeu os conceitos". | Item não verificável. | Troque por algo observável: um arquivo, uma execução, uma mensagem. |
| Termina com agradecimentos. | Créditos misturados ao conteúdo. | Mova para `files.credits`. |

## Entrega

- Seção ou capítulo de conclusão com resultado, conferência, retornos e próximo passo.
- Conferência testada com uma amostra pronta e uma incompleta.
- Prefácio revisado, se a promessa mudou.

## Checklist da entrega

- [ ] O resultado final está descrito de forma concreta e bate com a promessa do prefácio.
- [ ] Há uma conferência final com itens verificáveis.
- [ ] Cada item que pode falhar aponta para o capítulo que resolve, pelo título.
- [ ] O próximo passo usa apenas o que o livro ensinou.
- [ ] Links para fora foram conferidos.
- [ ] A conclusão não resume os capítulos nem termina em agradecimentos.
- [ ] A conferência distingue uma amostra pronta de uma incompleta.
- [ ] Se for capítulo próprio, está na última tabela de `[[chapters]]`.
- [ ] Links internos usam âncoras.

## Referências

- [Conferência final](references/conferencia-final.md): modelo de conferência, exemplo de encerramento e frases a evitar.

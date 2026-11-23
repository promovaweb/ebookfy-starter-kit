# Prefácio, créditos e autoria {#abertura-e-fechamento}

Além dos capítulos, a edição tem três textos editoriais: o prefácio, que abre o livro, e os créditos e a apresentação de autoria, que o fecham. Cada um é um arquivo Markdown em `editorial/`, declarado na tabela `[files]`:

```toml
[files]
preface = "editorial/prefacio.md"
credits = "editorial/creditos.md"
author = "editorial/autor.md"
```

O compilador monta a edição sempre na mesma ordem: prefácio, capítulos, créditos e autoria. Os três campos são obrigatórios na ficha, assim como a capa digital. Só o símbolo, `files.logo`, pode ficar de fora.

## O prefácio

O prefácio diz ao leitor, em poucos parágrafos, por que o livro existe e como aproveitá-lo. Ele responde a três perguntas:

1. Para quem é este livro?
2. O que o leitor vai conseguir fazer ao terminar?
3. Como ler: em ordem, por partes ou como consulta?

Um prefácio de guia cabe em uma página. Agradecimentos e histórias longas de bastidores ficam nos créditos ou fora do livro.

## A abertura e a conclusão

O primeiro capítulo apresenta o caminho do livro, como [Preparar a primeira edição](#preparar-a-primeira-edicao) faz com a lista das etapas. O último fecha o percurso com o que o leitor tem nas mãos e uma conferência curta do resultado. Evite resumir o livro capítulo por capítulo no fim: o leitor acabou de ler.

## Os créditos

Os créditos registram quem fez o livro e de onde vieram os materiais de terceiros. Use frases completas ou uma tabela curta:

| Função | Nome |
| --- | --- |
| Texto | Promovaweb |
| Revisão técnica | Nome da pessoa |
| Fontes do PDF | Inter e Manrope, sob a SIL Open Font License |

Cada imagem, citação ou trecho de outra obra precisa estar aqui, com a licença. O registro completo, com o endereço da fonte e a data da consulta, fica em `notas/atribuicoes.md`.

## A apresentação de autoria

A apresentação de autoria conta ao leitor quem escreveu o livro e por que essa pessoa entende do assunto. Escreva em terceira pessoa, com dois ou três parágrafos: a experiência que sustenta o livro, o trabalho atual e onde encontrar a pessoa. Quando a autoria é de uma empresa, como neste exemplo, apresente o que ela faz e onde o leitor acompanha o projeto.

---
name: ebookfy-10-autor
description: Escreve ou revisa a apresentação de autoria apontada por files.author, para autor individual, coautoria ou organização. Use quando a autoria mudar, quando a apresentação estiver genérica ou inflada, ou para conferir nomes, cargos, números e links antes da distribuição. Nunca atribui experiência sem fonte.
---

# Apresentar a autoria

A apresentação de autoria fecha a edição e responde a uma pergunta do leitor: por que confiar em quem escreveu isto? A resposta vem de fatos confirmados sobre a participação de cada pessoa na obra e sobre a experiência que dá sustentação ao conteúdo. Nada de adjetivos vazios nem conquistas sem fonte.

## Quando usar

- Livro novo, depois que a autoria estiver confirmada no briefing.
- Mudança em `book.authors`: entrada, saída ou troca de ordem.
- Apresentação genérica ("apaixonado por tecnologia"), inflada ou desatualizada.
- Conferência antes da distribuição: cargos, números e links mudam.

Participações que não são autoria (revisão, capa, ilustração) vão para os créditos, na etapa 09.

## Antes de começar

1. Leia `book.authors` e `book.publisher`.
2. Leia `files.author`, os créditos e o briefing.
3. Reúna o material fornecido pela pessoa: minibiografia, perfil profissional, lista de trabalhos. Use só o que veio dela ou de fonte pública verificável.

## Procedimento

1. **Defina o formato** pela assinatura: um parágrafo por pessoa (individual ou coautoria) ou uma apresentação institucional (organização). O título do arquivo aparece no sumário: "Sobre a autora", "Sobre os autores", "Sobre a Editora Exemplo".
2. **Responda a duas perguntas** com o [roteiro da apresentação](references/roteiro-da-apresentacao.md): qual foi a participação concreta de cada pessoa neste livro e que experiência dela sustenta o conteúdo.
3. **Use a ordem de `book.authors`.** Em coautoria, os parágrafos seguem a mesma ordem.
4. **Escreva com fatos.** Cargo atual, onde trabalha, há quanto tempo atua na área, projetos ou obras relacionados ao tema. Números (anos, alunos, projetos) só com fonte e data.
5. **Mantenha o foco no tema.** Experiência sem relação com o livro alonga o texto e não ajuda o leitor.
6. **Inclua canais de contato**, se a pessoa quiser: site, perfil profissional, email público. Confira cada link.
7. **Confira com a pessoa.** Envie o texto para aprovação. Grafia do nome, cargo e números precisam do aceite de quem é apresentado.
8. **Leia na prova.** A apresentação é a última seção editorial da edição. Confira em cada formato de `output.formats`.

## Regras do Ebookfy que afetam esta etapa

- O arquivo vem de `files.author` e é a última seção da edição, depois dos créditos. As notas de rodapé não entram nela: no PDF, cada nota fica no pé da página da chamada.
- Precisa existir e começar com um título `#`.
- `book.authors` alimenta os metadados de autoria do EPUB, do MOBI e do PDF. A grafia no texto e na ficha deve ser a mesma.
- A capa do PDF não mostra a autoria; quem procura o nome no PDF encontra aqui e nos metadados.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| "Referência nacional", "um dos maiores especialistas". | Adjetivo sem fato. | Troque pelo fato que sustenta: cargo, obra, tempo de atuação. |
| Número sem data ("mais de 10 mil alunos"). | Dado que muda. | Peça a fonte e a data, ou retire. |
| Nome escrito de forma diferente da ficha. | Grafias divergentes. | Use a grafia aprovada nos dois lugares. |
| Biografia de uma página. | Currículo completo colado. | Fique nas informações ligadas ao tema; um parágrafo por pessoa. |
| Experiência atribuída sem confirmação. | Texto completado por suposição. | Remova e pergunte à pessoa. |

## Entrega

- Arquivo de `files.author` com título e apresentação aprovada.
- Grafia dos nomes alinhada com `book.authors`.
- Links conferidos e números com fonte.

## Checklist da entrega

- [ ] O arquivo apontado por `files.author` existe e começa com um título `#`.
- [ ] Cada pessoa de `book.authors` tem apresentação, na mesma ordem e com a mesma grafia.
- [ ] A participação concreta de cada pessoa neste livro está dita.
- [ ] Toda experiência citada tem relação com o tema do livro.
- [ ] Cargos, números e datas têm fonte e estão atualizados.
- [ ] Não há adjetivo de autopromoção sem fato que o sustente.
- [ ] Links abrem e levam ao destino certo.
- [ ] A pessoa apresentada aprovou o texto.

## Referências

- [Roteiro da apresentação](references/roteiro-da-apresentacao.md): perguntas, exemplos para autoria individual, coautoria e organização, e trocas de adjetivo por fato.

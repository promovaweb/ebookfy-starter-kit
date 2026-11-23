---
name: ebookfy-01-organizar
description: Prepara um livro novo ou organiza uma pasta existente no padrão do Ebookfy. Use ao iniciar uma obra, ao receber um repositório desorganizado, ao preencher ou corrigir o ebook.toml, ou quando o CLI abrir o livro errado. Produz a ficha válida, a árvore de pastas e o briefing em notas/briefing.md.
---

# Organizar o projeto

Esta etapa deixa o livro pronto para as demais: uma ficha `ebook.toml` válida, capítulos em pastas próprias, materiais editoriais separados e um briefing que diz para quem o livro existe. Sem isso, pesquisa e redação começam sem destino e o compilador recusa a edição.

## Quando usar

- Repositório vazio que vai receber um livro novo.
- Pasta com material solto (rascunhos, imagens, um manuscrito) que precisa virar projeto Ebookfy. Se já existir um livro inteiro em outro formato, comece pela etapa 15 e volte aqui para revisar a ficha.
- `ebookfy info` falha, mostra outro livro ou lista capítulos fora da ordem esperada.
- A autoria, o título, a versão ou os formatos da edição mudaram.

Passe para a etapa 02 quando a ficha estiver válida e o briefing registrar as perguntas que ainda dependem de fonte. Passe para a etapa 03 quando o assunto já estiver apurado e faltar apenas a ordem de leitura.

## Antes de começar

1. Confirme a pasta de trabalho com a pessoa. Um livro mora na pasta que contém o `ebook.toml`, que não precisa ser a raiz do repositório.
2. Rode `ebookfy --version`. As instruções desta skill valem para o CLI 0.5 ou superior.
3. Rode `ebookfy doctor` e anote se Pandoc, WeasyPrint e `ebook-convert` estão disponíveis. A ausência deles não impede organizar, mas define quais formatos poderão ser testados.

## Procedimento

1. **Localize ou crie a ficha.** Em repositório Git vazio, rode `ebookfy init`. O comando copia o starter kit com ficha, capítulo ilustrado, materiais editoriais e as skills instaladas, e recusa pastas com arquivos. Em pasta existente, procure `ebook.toml`. O CLI sobe pelas pastas a partir do diretório atual até achar uma ficha e para na raiz do repositório Git, então um TOML esquecido numa pasta acima pode capturar a consulta.
2. **Monte a árvore padrão.** Use a estrutura da referência [Mapa do projeto](references/mapa-do-projeto.md): `capitulos/<NN-slug>/CHAPTER.md` com `imagens/` ao lado, `editorial/` para capa, prefácio, créditos e autoria, `notas/` para os registros de trabalho e a pasta de saída declarada em `output.directory`. Mova arquivos com `git mv` para preservar o histórico.
3. **Escreva o briefing** em `notas/briefing.md`, seguindo o [modelo de briefing](references/modelo-de-briefing.md). Responda com frases concretas: quem lê, o que essa pessoa já sabe, o que conseguirá fazer ao terminar, qual o tom, quais formatos serão entregues e quem aprova título e autoria. Use o que a pessoa informou e marque como pendente o que ninguém confirmou.
4. **Preencha a ficha** a partir do briefing. Todos os campos de `[book]` são obrigatórios, exceto `subtitle`. Confira a grafia de título e autoria com quem assina. Escolha `slug` e `identifier` uma vez e preserve-os nas edições seguintes, porque o slug nomeia os arquivos e o identificador marca a obra nos leitores.
5. **Declare os capítulos.** Uma tabela `[[chapters]]` por `CHAPTER.md`, na ordem de leitura. Notas, rascunhos e pesquisa nunca entram na lista.
6. **Confira pelo CLI.** Rode `ebookfy info --json` de dentro de uma pasta de capítulo. Compare título, idioma, versão, formatos e a ordem dos títulos com o briefing. Rode `ebookfy` para ver o sumário na TUI.
7. **Registre o que falta.** Liste no fim do briefing as afirmações que precisam de fonte (etapa 02), os capítulos que ainda não existem (etapa 03) e os materiais sem autorização de uso (etapa 09).

## Regras do Ebookfy que afetam esta etapa

- A ficha rejeita campos desconhecidos. Erros de digitação como `autors` ou `format` derrubam a leitura.
- `book.version` segue `X.Y.Z`, `book.date` usa `AAAA-MM-DD` e `book.slug` aceita apenas minúsculas sem acento, números e hífen.
- `files.cover`, `files.preface`, `files.credits` e `files.author` são obrigatórios e precisam existir. `files.logo` é opcional; sem ele, o PDF usa a capa no espaço do símbolo.
- Todo capítulo termina em `CHAPTER.md`, com essa caixa. Prefácio, capítulos, créditos e autoria precisam de um título `#` de nível 1 e não podem repetir arquivo.
- Caminhos são relativos à pasta do TOML e não podem sair dela, nem por link simbólico.
- `output.formats` aceita `pdf`, `epub` e `mobi`, sem repetição.
- Preferências do terminal ficam em `~/.ebookfy/` (`ebookfy config list`) e não fazem parte do livro. Nunca grave credenciais na pasta da obra.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| `Nenhum ebook.toml foi encontrado` | O terminal está fora da pasta do livro ou a ficha está em outro repositório. | Entre na pasta do livro ou em uma subpasta dele. |
| `info` mostra outro título | Há um `ebook.toml` numa pasta intermediária. | Rode `ebookfy info --json`, veja qual livro abriu e remova ou mova a ficha extra. |
| Erro em JSON com `unrecognized_keys` e `Unrecognized key: "..."` | Campo inexistente ou com erro de digitação. | Compare com a tabela de campos do [Mapa do projeto](references/mapa-do-projeto.md). |
| Erro em JSON com `invalid_type` e um `path` como `book.authors` | Campo obrigatório ausente ou com tipo errado (texto no lugar de lista). | Preencha o campo indicado em `path` no formato da tabela. |
| Erro em JSON com `invalid_format` ou `too_small` | Data, versão ou slug fora do formato, ou lista vazia. | Corrija para `AAAA-MM-DD`, `X.Y.Z`, minúsculas com hífen, ou acrescente um item. |
| `Cada capítulo precisa de CHAPTER.md` | Arquivo com outro nome ou caixa diferente. | Renomeie para `CHAPTER.md` e ajuste a tabela. |
| `Inclua um título de nível 1` | O arquivo não tem nenhum título `#`, ou o único `#` está dentro de um bloco de código. | Abra o arquivo com uma linha `# Título`. Texto antes do título é aceito pelo CLI, mas a convenção é começar pelo título. |
| `Caminho fora do projeto` | Caminho absoluto, `../` ou link que aponta para fora. | Copie o material para dentro do livro. |
| `ebookfy init` recusa a pasta | A pasta já tem arquivos. | Use um repositório vazio ou organize manualmente com o mapa. |

## Entrega

- `ebook.toml` válido, conferido por `ebookfy info --json`.
- Árvore no padrão do mapa, com movimentações feitas por `git mv`.
- `notas/briefing.md` preenchido, com as pendências separadas por etapa.
- Um resumo para a pessoa: o que foi criado, o que foi movido e o que falta confirmar.

## Checklist da entrega

- [ ] `ebookfy info --json` devolve `ok: true` quando executado de dentro de um capítulo.
- [ ] Título, subtítulo e autoria seguem a grafia confirmada por quem assina.
- [ ] `slug`, `identifier` e `version` foram escolhidos de forma deliberada e anotados no briefing.
- [ ] Cada capítulo listado tem pasta própria, `CHAPTER.md` e título de nível 1.
- [ ] Prefácio, créditos, autoria e capa existem nos caminhos de `[files]`.
- [ ] Notas, rascunhos e pesquisa ficam em `notas/` e não aparecem em `[[chapters]]`.
- [ ] Nenhum arquivo foi apagado ou sobrescrito sem confirmação; movimentações preservam o histórico.
- [ ] O briefing descreve leitor, ponto de partida, resultado final, tom e formatos.
- [ ] As pendências de fonte, de capítulo e de autorização estão listadas para as etapas 02, 03 e 09.
- [ ] `ebookfy doctor` foi executado e os conversores ausentes estão anotados.

## Referências

- [Mapa do projeto](references/mapa-do-projeto.md): árvore padrão, campos da ficha e onde cada registro de trabalho fica.
- [Modelo de briefing](references/modelo-de-briefing.md): perguntas do briefing com um exemplo preenchido.

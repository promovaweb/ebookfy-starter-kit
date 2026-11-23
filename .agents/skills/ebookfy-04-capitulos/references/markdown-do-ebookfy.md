# Markdown do Ebookfy

O compilador junta prefácio, capítulos, créditos e autoria num único documento Pandoc, nessa ordem, e gera os formatos a partir dele. Por isso, algumas regras valem para o livro inteiro e não só para o capítulo: ids de títulos e rótulos de notas precisam ser únicos na obra.

Qualquer aviso do Pandoc derruba o build (`--fail-if-warnings`). Isso é bom: imagem ausente, nota duplicada ou id repetido aparece na hora, não no leitor. Links para âncoras inexistentes e para outros arquivos não geram aviso; confira os destinos na prova (etapa 12).

## Estrutura

```markdown
# Agendar a execução

Parágrafo de abertura.

## Trocar o gatilho

### Ajustar o fuso horário
```

- Um único `#` por arquivo: é o título no sumário.
- `##` e `###` para seções. Evite `####` ou mais: a navegação dos leitores digitais fica confusa.
- Não use frontmatter YAML (`---` no topo). Ele não é lido como metadado: as linhas viram Markdown comum e podem aparecer como texto, linha horizontal ou tabela, até no fim da seção anterior.

## Ênfase, listas e citações

```markdown
Use **negrito** para o nome de um botão e *itálico* para um termo novo.

1. Abra o editor.
2. Clique em **Add first step**.

- Item sem ordem
- Outro item

- [ ] Item de checklist (aparece como caixa de seleção)

> Citação em bloco. Use para trechos citados de uma fonte, não para destaque.
```

Deixe uma linha em branco antes e depois de listas, citações, tabelas e blocos de código.

## Código

````markdown
Na pasta do projeto, rode:

```bash
docker compose up -d
```

O terminal mostra `Container n8n  Started`.
````

- Sempre declare a linguagem (`bash`, `json`, `yaml`, `toml`, `javascript`, `text`). Ela ativa o realce de sintaxe no PDF e no EPUB a partir do Ebookfy 0.5; leitores de EPUB que ignoram o estilo do livro mostram o código sem cores.
- Código inline com crases: `ebookfy info`.
- Linhas muito longas quebram mal no MOBI e no PDF A4. Quebre comandos longos com `\` no fim da linha.

## Tabelas

```markdown
| Campo | Exemplo |
| --- | --- |
| book.slug | primeiros-fluxos-n8n |
```

Tabelas com mais de quatro colunas ou células longas ficam ilegíveis em telas pequenas. Prefira lista ou divida em duas tabelas.

## Figuras

```markdown
![Editor do n8n com o Schedule Trigger selecionado](imagens/schedule-trigger.png)
```

- O caminho é relativo ao `CHAPTER.md`. Guarde a imagem em `imagens/` do capítulo: o CLI aceita caminhos para fora do livro, mas o livro deixa de compilar em outra máquina.
- Uma imagem sozinha no parágrafo vira figura, e o texto entre colchetes aparece como **legenda visível** e como texto alternativo. Escreva uma legenda que diga o que observar.
- Uma imagem no meio de uma frase fica inline e não ganha legenda. Use só para ícones pequenos.
- Largura: `![Legenda](imagens/arquivo.png){width=60%}`. Use para capturas pequenas que ficariam esticadas.

Detalhes de preparo das figuras estão na etapa 05.

## Links

| Destino | Como escrever | Resultado |
| --- | --- | --- |
| Site externo | `[documentação do n8n](https://docs.n8n.io/)` | Funciona nos três formatos. |
| Título de outro capítulo | `[Agendar a execução](#agendar-a-execução)` | Funciona; o leitor vai até o título. |
| Âncora explícita | `## Ajustar o fuso {#fuso-horario}` e `[fuso](#fuso-horario)` | Funciona e não quebra se o título mudar. |
| Arquivo de outro capítulo | `[cap. 3](../03-agendar/CHAPTER.md)` | **Não use.** Compila, mas fica quebrado na edição. |

O id automático de um título é o texto sem formatação, em minúsculas, sem pontuação, com espaços trocados por hífen e acentos preservados; números e símbolos antes da primeira letra são descartados. `## Agendar a execução` vira `#agendar-a-execução`; `## 3. Usar o **Set**!` vira `#usar-o-set`. Na dúvida, procure o id no EPUB gerado (`unzip -p` do capítulo) ou defina um explícito. Títulos iguais em capítulos diferentes recebem sufixo (`exemplo`, `exemplo-1`), e um link para `#exemplo` sempre leva ao primeiro. Toda seção que receber link de outro lugar deve ter id explícito com `{#...}`.

## Notas de rodapé

```markdown
O limite pode mudar entre versões.[^cap03-limite]

[^cap03-limite]: Conferido na versão 2.3.1 em novembro de 2026.
```

Os rótulos das notas valem para o livro inteiro. Duas definições `[^1]:` em capítulos diferentes derrubam o build com `Duplicate note reference`; duas chamadas para uma mesma definição compilam, mas apontam para a mesma nota. Use um prefixo por capítulo: `[^cap03-limite]`.

## Blocos com classe

```markdown
::: aviso
Faça backup do banco antes de atualizar.
:::
```

O bloco vira uma `div` com a classe no PDF e no EPUB. O kit de impressão não define estilo para classes próprias, então o bloco aparece como parágrafo comum. Para destacar um aviso, prefira começar o parágrafo com **Atenção:** em negrito.

## O que evitar

- HTML embutido: funciona no PDF e no EPUB, mas costuma quebrar no MOBI.
- Imagens remotas (`https://...png`): o Pandoc baixa a imagem a cada build. Sem rede, o build falha; se o endereço mudar, a figura muda ou some.
- Emojis como marcadores de seção: nem todas as fontes do PDF têm os glifos.
- Títulos com formatação (`## Usar o **Set**`): o sumário mostra os símbolos em alguns leitores.

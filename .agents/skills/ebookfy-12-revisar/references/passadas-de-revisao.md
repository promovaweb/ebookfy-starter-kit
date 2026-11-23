# Passadas de revisão

Cada passada procura um tipo de problema. Misturar todas numa leitura só faz a atenção cair nas vírgulas e perder os saltos de raciocínio.

## 1. Percurso

Leia na ordem da edição, como o leitor. Pergunte em cada seção:

- O leitor sabe o que está fazendo e por quê?
- Este termo já apareceu antes, com explicação?
- Este passo depende de algo que o texto ainda não pediu?
- O resultado de cada etapa importante está descrito?
- O capítulo começa onde o anterior terminou?
- O tratamento (você, tu, impessoal) e o tom seguem o briefing?

## 2. Exemplos

Execute em ambiente limpo, na ordem do texto, copiando dos blocos de código do próprio livro.

- O comando roda na pasta indicada?
- A saída bate com a descrita?
- Valores de exemplo são consistentes entre capítulos (mesmo nome de planilha, mesma porta, mesmo usuário)?
- Nomes de botões e menus batem com a versão citada?

## 3. Fontes

- Toda afirmação verificável tem entrada em `notas/fontes.md`?
- Números que mudam com o tempo trazem data?
- Entradas `pendente` da ficha viraram texto como se estivessem confirmadas?

## 4. Mecânica

Comandos úteis, rodados na pasta do livro:

```bash
# capítulos com quantidade de títulos de nível 1 diferente de um (ignora blocos de código)
for f in capitulos/*/CHAPTER.md; do
  n=$(awk '/^(```|~~~)/{c=!c} !c && /^# /{n++} END{print n+0}' "$f")
  [ "$n" -ne 1 ] && echo "$f: $n títulos #"
done

# links para arquivos .md, com ou sem âncora (ficam quebrados na edição)
grep -rnE '\]\([^)#]*\.md(#[^)]*)?\)' capitulos/ editorial/

# frontmatter YAML no topo
for f in capitulos/*/CHAPTER.md; do head -1 "$f" | grep -q '^---' && echo "$f"; done

# figuras sem legenda
grep -rn '!\[\](' capitulos/

# cercas de bloco sem linguagem (inclui os fechamentos)
grep -rn '^```$' capitulos/ editorial/

# definições de nota repetidas no livro (capítulos e textos editoriais)
grep -rhoE '^\[\^[^]]+\]:' capitulos/ editorial/ | sort | uniq -d

# referências por número de capítulo, que quebram ao reordenar
grep -rniE 'cap[íi]tulo [0-9]+' capitulos/ editorial/
```

A busca por cercas sem linguagem também encontra as cercas de fechamento; confira cada ocorrência de abertura.

Depois da mecânica, compile:

```bash
ebookfy build --json
```

## 5. Prova nos formatos

Abra os arquivos recém-gerados e leia:

- o sumário, conferindo títulos e ordem;
- um capítulo com figura, tabela e bloco de código;
- uma nota de rodapé: abra a nota e volte pelo recurso que o leitor oferece (no PDF, as notas ficam no fim do documento);
- um link interno entre capítulos;
- os créditos e a autoria.

No EPUB, aumente a fonte em dois níveis e confira se tabelas e figuras continuam legíveis.

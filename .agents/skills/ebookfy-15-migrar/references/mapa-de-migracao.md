# Mapa de migração

> O exemplo usa um livro fictício, *Primeiros fluxos no n8n*, vindo de um manuscrito único.

Grave em `notas/migracao.md`. O mapa é preenchido antes de mover os arquivos e completado ao fim com o resultado.

## Formato

```markdown
# Migração · Primeiros fluxos no n8n

Origem: notas/origem/manuscrito.md (convertido de manuscrito.docx com Pandoc 3.10)
Edição de referência: notas/origem/manuscrito.pdf
Data: 2026-11-23

## Mapa

| # | Origem | Destino | Observações |
| --- | --- | --- | --- |
| P | "Antes de começar" (linhas 1 a 40) | editorial/prefacio.md | Título trocado para "Prefácio". |
| 01 | "# Instalação" | capitulos/01-instalar/CHAPTER.md | 3 figuras; 1 nota. |
| 02 | "# Seu primeiro workflow" | capitulos/02-primeiro-fluxo/CHAPTER.md | 4 figuras. |
| 03 | "# Agendamento" + "## Fuso horário" de "# Dicas" | capitulos/03-agendar/CHAPTER.md | Seção movida de "Dicas" por depender do cap. 03. |
| 04 | "# Planilhas" | capitulos/04-planilha/CHAPTER.md | Tabela larga; revisar no MOBI. |
| X | "# Dicas" (restante) | notas/origem/dicas-nao-usadas.md | Fora da edição, a pedido da Ana. |
| C | "Agradecimentos" | editorial/creditos.md | Lista de equipe completada com a revisão técnica. |
| A | "Sobre a autora" | editorial/autor.md | Sem mudanças. |
| Capa | capa-final.jpg | editorial/capa.jpg | |

## Conversões aplicadas
- Frontmatter (title, author, date) levado para [book] e removido.
- Notas [^1] a [^12] renomeadas para [^cap01-1] etc.
- Links "veja o capítulo Agendamento" convertidos para [Agendar a execução](#agendar-a-execução).
- Imagens de media/ redistribuídas em imagens/ de cada capítulo.

## Resultado
- ebookfy info: 4 capítulos, na ordem do mapa.
- ebookfy build: ok, sem aviso.
- Comparação com a referência: 4 capítulos e 14 figuras dos dois lados; início e fim dos capítulos 01 e 04 conferidos; nota 7 conferida.
- Lacunas: o capítulo 04 cita "a planilha de exemplo" que não veio na origem.
- Para revisão (etapa 12): títulos de capítulo ainda em forma de rótulo; tom muda no capítulo 04.
```

## Por que mapear antes de mover

- Mostra trechos que ninguém sabia para onde iam, como as "Dicas".
- Evita perder seções no meio da divisão.
- Permite conferir no fim, tabela contra tabela, sem reler o livro inteiro.
- Responde, meses depois, de onde veio um parágrafo.

## Contagens para comparar

```bash
# figuras na origem (Markdown e HTML que a conversão de DOCX pode gerar) e no projeto novo
grep -oE '!\[|<img ' notas/origem/manuscrito.md | wc -l
grep -rhoE '!\[|<img ' capitulos/ editorial/ | wc -l

# notas de rodapé (definições), incluindo os textos editoriais
grep -oE '^\[\^[^]]+\]:' notas/origem/manuscrito.md | wc -l
grep -rhoE '^\[\^[^]]+\]:' capitulos/ editorial/ | wc -l
```

Diferença nas contagens é pendência até ser explicada no mapa.

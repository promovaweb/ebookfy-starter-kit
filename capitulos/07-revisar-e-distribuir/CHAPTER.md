# Revisar e distribuir {#revisar-e-distribuir}

A edição compilou e passou pela conferência. Falta a última leitura, fechar a versão e entregar os arquivos certos. Este capítulo também encerra o livro com o que você tem agora.

## Revisar em passadas

Uma revisão rende mais em passadas curtas, cada uma com um foco, do que numa leitura única tentando ver tudo:

1. **Conteúdo**: cada capítulo cumpre o que o sumário promete.
2. **Fatos**: comandos, números e nomes de telas conferem com `notas/fontes.md`.
3. **Texto**: frases claras, termos consistentes, sem repetição.
4. **Edição**: figuras, legendas, links e notas no lugar, nos três formatos.

Registre cada achado e a correção em `notas/revisao.md`. Depois de corrigir, compile e confira de novo.

## Fechar a versão

A versão da edição fica em `book.version` e aparece no nome dos arquivos e na capa do PDF. Use três números:

| Mudança | Exemplo |
| --- | --- |
| Correção de erro de digitação ou de link | `0.1.0` para `0.1.1` |
| Seção ou capítulo novo | `0.1.1` para `0.2.0` |
| Livro reescrito ou reorganizado | `0.2.0` para `1.0.0` |

Atualize também `book.date` com a data da edição. Cada build grava a data da compilação dentro dos arquivos, por isso dois builds da mesma versão geram arquivos com bytes diferentes.

## Entregar os arquivos conferidos

Entregue exatamente os arquivos que passaram pela conferência. Para isso, guarde a saída do build em `notas/build.json`:

```bash
ebookfy build --json > notas/build.json
```

O arquivo lista o caminho de cada formato gerado. Depois de conferir, não compile de novo antes de entregar. Se precisar corrigir algo, a correção volta para a revisão e gera uma nova conferência.

Na entrega, mande o PDF para quem lê no computador ou imprime, o EPUB para os leitores digitais e o MOBI só para quem usa um Kindle antigo. Registre em `notas/entrega.md` para onde foi cada arquivo e quando.

## O que você tem agora

Você tem um projeto de livro que compila em PDF, EPUB e MOBI a partir do mesmo texto. A ficha guarda os dados da edição, cada capítulo mora na sua pasta com as imagens, e a pasta `notas/` registra o planejamento, a revisão e a entrega.

Para começar o seu livro, troque o título na ficha, apague os capítulos deste exemplo e crie o primeiro capítulo seu. A skill `ebookfy-01-organizar` conduz essa primeira etapa e chama as seguintes na ordem.

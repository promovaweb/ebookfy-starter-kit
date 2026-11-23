# Diagnóstico do build

O `ebookfy build` valida a ficha antes de chamar qualquer conversor. Erros de ficha aparecem primeiro; erros de conversão começam com o nome do programa.

## Erros da ficha

| Mensagem | Causa | Correção |
| --- | --- | --- |
| `Nenhum ebook.toml foi encontrado` | Fora da pasta do livro. | Entre na pasta do livro ou numa subpasta. |
| Lista JSON com `code` e `path` (`unrecognized_keys`, `invalid_type`, `invalid_format`, `too_small`) | Campo desconhecido, ausente, com formato errado ou lista vazia. O `path` indica a tabela ou o campo; em `unrecognized_keys`, `keys` traz os nomes rejeitados. | Compare com a tabela de campos da etapa 01. |
| `Cada seção e formato deve aparecer uma vez.` | Arquivo repetido entre `[files]` e `[[chapters]]` ou formato repetido. | Remova a repetição. |
| `Cada capítulo precisa de CHAPTER.md.` | Tabela apontando para outro nome de arquivo. | Renomeie o arquivo e a tabela. |
| `Esperado arquivo: ...` | O caminho aponta para uma pasta. | Aponte para o arquivo. |
| `Duas seções apontam ao mesmo arquivo.` | Dois caminhos diferentes chegam ao mesmo arquivo, por exemplo por link. | Use um arquivo por seção. |
| `Inclua um título de nível 1 em ...` | Arquivo sem nenhum `#`, ou com o único `#` dentro de bloco de código. | Abra o arquivo com `# Título`. |
| `Caminho fora do projeto: ...` | Caminho absoluto, com `../` para fora ou link simbólico externo. | Traga o arquivo para dentro do livro. |
| `A saída precisa ficar em uma pasta local do projeto.` | `output.directory` passa por link simbólico. | Use uma pasta real. |

## Erros do Pandoc

| Mensagem | Causa | Correção |
| --- | --- | --- |
| `Could not fetch resource capitulos/.../x.png` | Figura ausente, caixa diferente ou caminho errado. | Confira o nome exato do arquivo. |
| `Duplicate note reference '1'` | A mesma definição de nota (`[^1]:`) em dois arquivos do livro. | Prefixe os rótulos: `[^cap03-limite]`. |
| `Duplicate identifier` | Dois títulos com o mesmo id explícito `{#id}`. | Torne os ids únicos no livro. |
| `Failing because there were warnings.` | Qualquer aviso do Pandoc. | Leia a linha `[WARNING]` acima e corrija a causa. |
| Programa não encontrado | Pandoc fora do PATH. | Instale e confira com `ebookfy doctor`. |

## Erros do WeasyPrint (PDF)

| Sintoma | Causa | Correção |
| --- | --- | --- |
| Programa não encontrado | WeasyPrint ausente. | Instale e confira com `ebookfy doctor`. |
| Erro ao carregar imagem | Formato não suportado ou arquivo corrompido. | Reexporte a figura em PNG ou JPEG. |
| PDF gerado, mas com fonte diferente | Fonte do kit não carregada. | Reinstale o Ebookfy; o kit fica em `print/fonts/`. |

## Erros do ebook-convert (MOBI)

| Sintoma | Causa | Correção |
| --- | --- | --- |
| Programa não encontrado | Calibre ausente ou `ebook-convert` fora do PATH. | Instale o Calibre e confira com `ebookfy doctor`. No macOS, o binário fica dentro do aplicativo e precisa ser incluído no PATH. |
| Conversão lenta ou travando | EPUB grande, com imagens pesadas. | Reduza as figuras (etapa 05). |
| Tabela quebrada no MOBI | Limite do formato. | Simplifique a tabela ou troque por lista. |

## Roteiro de investigação

1. Rode `ebookfy build` e copie a primeira linha de erro.
2. Identifique o programa pelo início da mensagem.
3. Se for erro de ficha, rode `ebookfy info --json` para ver a mesma validação.
4. Se for Pandoc, procure a linha `[WARNING]` e o arquivo e linha citados.
5. Corrija na fonte (`CHAPTER.md`, imagem, ficha), nunca no arquivo gerado.
6. Compile de novo e confirme que a mensagem sumiu antes de procurar o próximo erro.
7. Para isolar um formato, mude temporariamente `output.formats` para só ele, compile e volte a lista ao normal.

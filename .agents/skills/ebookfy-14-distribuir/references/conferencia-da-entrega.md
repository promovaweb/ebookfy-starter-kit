# Conferência da entrega

> O modelo de registro usa um livro fictício, *Primeiros fluxos no n8n*. Hashes e links ilustram o formato.

## Relacionar os exemplares

Na raiz do livro, a partir do `notas/build.json` gravado na etapa 13. Não recompile aqui: o MOBI sai com hash novo a cada build, e o PDF e o EPUB mudam quando a versão de um conversor muda.

```bash
jq -r '.data.arquivos[]' notas/build.json | while read -r f; do
  printf '%s\t%s\t%s\n' "$f" "$(stat -c %s "$f")" "$(sha256sum "$f" | cut -d' ' -f1)"
done
```

No macOS, troque `stat -c %s` por `stat -f %z` e `sha256sum` por `shasum -a 256`.

## Conferir a cópia baixada

```bash
sha256sum ~/Downloads/primeiros-fluxos-n8n-v1.0.0.pdf
```

O valor precisa ser igual ao registrado. Se for diferente, não distribua até descobrir por quê.

Alguns destinos alteram o arquivo (recompressão de PDF, remoção de metadados). Nesse caso, o hash não vai bater por motivo conhecido: registre o destino como "altera o arquivo", abra a cópia baixada e confira capa, versão, sumário e uma figura.

## Modelo de registro

Grave em `notas/entrega.md`, abaixo da prova da etapa 13:

```markdown
## Entrega · edição 1.0.0 · 2026-11-24

Autorização: Ana, por email em 2026-11-23, para a área do aluno da turma de março.

| Formato | Arquivo | Tamanho | SHA-256 |
| --- | --- | --- | --- |
| PDF | ebook/primeiros-fluxos-n8n-v1.0.0.pdf | 2 418 332 | 9f2c...e41a |
| EPUB | ebook/primeiros-fluxos-n8n-v1.0.0.epub | 1 102 870 | 47ab...0c93 |

Destino: área do aluno, módulo "Material de apoio".
Links:
- PDF: https://exemplo.com/aluno/material/primeiros-fluxos-n8n-v1.0.0.pdf
- EPUB: https://exemplo.com/aluno/material/primeiros-fluxos-n8n-v1.0.0.epub

Testes de acesso:
- Conta de aluno da turma: baixou os dois; hashes iguais aos locais; capa mostra edição 1.0.0.
- Conta sem matrícula: acesso negado nos dois links.

Edição anterior: nenhuma (primeira edição).
```

## Se o pedido for só preparar

Entregue à pessoa:

- os caminhos dos arquivos;
- a tabela de tamanhos e hashes;
- o que deve ser conferido depois do envio (baixar pelo caminho do leitor e comparar o hash).

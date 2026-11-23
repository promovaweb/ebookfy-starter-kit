# Versões e substituição

## Numerar a edição

`book.version` usa `X.Y.Z`. Uma convenção que funciona para livros:

| Mudança | Versão | Exemplo |
| --- | --- | --- |
| Correção de erro de digitação, link ou figura, sem mudar o conteúdo | Z | 1.0.0 para 1.0.1 |
| Seção nova, capítulo atualizado para nova versão de ferramenta | Y | 1.0.1 para 1.1.0 |
| Reestruturação, novo público, nova edição | X | 1.1.0 para 2.0.0 |

Atualize também `book.date`. O `book.identifier` continua o mesmo: é a mesma obra. Livros com ISBN podem precisar de ISBN novo para edição nova; confira as regras da agência.

## Nunca recompile uma versão distribuída

Se a 1.0.0 já chegou a leitores, qualquer correção vira 1.0.1. Duas versões diferentes com o mesmo número tornam impossível saber qual o leitor tem.

## Substituir uma edição distribuída

1. Aumente `book.version` e `book.date`, compile e faça a prova (etapa 13).
2. Envie os arquivos novos com o nome novo.
3. Troque os links públicos para os arquivos novos.
4. Decida com a pessoa responsável o destino da versão anterior: remover, manter com aviso de que há versão nova ou arquivar.
5. Avise quem já tinha a edição anterior, quando o canal permitir, dizendo o que mudou.
6. Registre a troca em `notas/entrega.md`.

## Registrar o que mudou

Mantenha uma lista curta por versão em `notas/entrega.md`. Ela vira o aviso aos leitores.

```markdown
## Mudanças da 1.0.1
- Capítulo 03: o passo de ativação descreve a chave "Inactive" como aparece no n8n 2.3.
- Capítulo 05: inclui a criação da credencial SMTP.
- Créditos: corrige a grafia do nome do revisor técnico.
```

Se o livro tiver uma página de "Histórico de edições" para o leitor, ela é um capítulo comum no fim de `[[chapters]]` ou uma seção nos créditos.

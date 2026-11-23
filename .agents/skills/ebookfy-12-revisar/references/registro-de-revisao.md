# Registro de revisão

> Os exemplos usam um livro fictício, *Primeiros fluxos no n8n*.

Grave em `notas/revisao.md`. Uma seção por rodada de revisão, com data e escopo, e um bloco por achado.

## Formato

```markdown
# Revisão · 2026-11-23 · edição 1.0.0

## Escopo
- Lido: prefácio, capítulos 01 a 07, créditos, autoria.
- Executado: todos os exemplos dos capítulos 01 a 05, em n8n 2.3.1 com Docker 27.3.
- Fora do escopo: exemplos do capítulo 06 (falta acesso ao SMTP de teste).
- Pedido: diagnóstico e correção.

## Achados

### R-01 · impede · corrigido
- Local: capitulos/03-agendar/CHAPTER.md, seção "Ativar e conferir".
- Trecho: "Clique na chave Active."
- O que acontece: na versão 2.3, a chave mostra "Inactive" até ser clicada. O leitor procura "Active" e não encontra.
- Correção: "Clique na chave **Inactive** no topo do editor; ela muda para **Active**."
- Verificação: refeito o passo em instância limpa; o texto agora descreve o que aparece.

### R-02 · atrapalha · aberto
- Local: capitulos/05-email/CHAPTER.md, primeiro parágrafo.
- Trecho: "Use a credencial SMTP que você já tem."
- O que acontece: nenhum capítulo anterior cria credencial SMTP.
- Correção proposta: incluir a criação da credencial no início do capítulo 05.
- Responsável: Ana (decide se o passo entra no 05 ou na introdução).

### R-03 · ajuste · corrigido
- Local: capitulos/02-primeiro-fluxo/CHAPTER.md, figura do canvas.
- Trecho: `![canvas](imagens/canvas.png)`
- O que acontece: a legenda impressa é só "canvas".
- Correção: `![Canvas com Manual Trigger ligado ao node Set](imagens/canvas.png)`
- Verificação: build sem aviso, legenda conferida no EPUB.

## Resumo
- Impede: 1 (corrigido).
- Atrapalha: 1 (aberto, com responsável).
- Ajuste: 1 (corrigido).
- Build: sem aviso. Prova lida: PDF e EPUB, capítulos 02 e 03 e créditos.
```

## Gravidade

| Gravidade | Significa | Exemplo |
| --- | --- | --- |
| `impede` | O leitor não consegue seguir ou recebe informação errada. | Comando que falha; passo faltando; afirmação falsa. |
| `atrapalha` | O leitor consegue, mas trava, volta ou desconfia. | Termo sem explicação; figura que não mostra o detalhe. |
| `ajuste` | Melhora a leitura sem mudar o resultado. | Legenda fraca; frase longa; repetição. |

Uma edição com achado `impede` aberto não deve ser distribuída.

## Diagnóstico de figura que só falha num formato

Se a imagem aparece no PDF e some no EPUB, confira primeiro o caminho e o formato do arquivo (WebP, SVG com fonte externa) antes de mudar o texto. Se a figura aparece, mas o leitor continua errando o passo, o problema é a ligação entre texto e detalhe visual: revise o parágrafo e a legenda.

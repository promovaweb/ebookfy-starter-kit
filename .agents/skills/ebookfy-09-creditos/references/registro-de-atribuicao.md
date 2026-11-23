# Registro de atribuição

> Os exemplos usam um livro fictício, *Primeiros fluxos no n8n*. Nomes, links e licenças ilustram o formato.

Grave em `notas/atribuicoes.md`. Uma linha por arquivo usado na edição ou por material de terceiro citado no texto. O registro é a fonte do texto de créditos.

## Formato

```markdown
| Arquivo ou trecho | Tipo | Autor ou origem | Condição de uso | Crédito exigido | Situação |
| --- | --- | --- | --- | --- | --- |
| editorial/capa.png | capa | Equipe da Editora Exemplo | própria | não | ok |
| capitulos/02-primeiro-fluxo/imagens/canvas.png | captura | Equipe, n8n 2.3 em ambiente de testes | própria | não | ok |
| capitulos/04-planilha/imagens/escritorio.jpg | foto | Maria Lima, banco Exemplo Fotos, id 48213 | licença do banco, uso comercial, sem atribuição obrigatória | não | ok |
| capitulos/06-erros/imagens/fluxo-erros.png | diagrama | Adaptado de João Reis, "Padrões de erro", 2025 | CC BY 4.0 | "Adaptado de João Reis, Padrões de erro, CC BY 4.0" | ok |
| capitulos/03-agendar/imagens/slide-aula.png | diagrama | Slide de palestra de terceiro | sem autorização | não se aplica | pendente |
| Citação no cap. 05 | citação | Documentação oficial do n8n | citação curta com fonte | link para a página | ok |
| Fontes Inter e Manrope | tipografia | Rasmus Andersson; Mikhail Sharanda | SIL OFL 1.1 | nome e licença | ok |
```

Situação usa `ok`, `pendente` ou `substituir`.

## Por tipo de material

| Material | O que registrar |
| --- | --- |
| Captura de tela própria | Ferramenta e versão, data, ambiente de demonstração usado. |
| Foto própria | Quem fotografou, autorização de pessoas reconhecíveis. |
| Banco de imagens | Nome do banco, identificador da imagem, tipo de licença, data do download. |
| Creative Commons | Autor, título, link, licença com versão, se houve alteração. |
| Autorização direta | Quem autorizou, quando, por qual meio, o que foi autorizado (uso, canal, prazo). Guarde a mensagem em `notas/autorizacoes/`. |
| Ilustração encomendada | Quem fez, contrato ou acordo, se há cessão de direitos. |
| Fonte tipográfica | Família, autor, licença. |
| Trecho de código de terceiro | Repositório, licença, se foi alterado. |

## Pessoas reconhecíveis em fotos

Foto com pessoa reconhecível precisa de autorização de uso de imagem dela. Registre como na autorização direta. Sem autorização, recorte, desfoque de forma que não identifique ou troque a foto.

## Licenças Creative Commons em livro

| Licença | Uso num livro vendido | Uso com adaptação |
| --- | --- | --- |
| CC0 | Sim | Sim |
| CC BY | Sim, com crédito | Sim, indicando a alteração |
| CC BY-SA | Sim, com crédito | Sim, mas a adaptação herda a licença |
| CC BY-ND | Sim, com crédito | Não |
| CC BY-NC (e variações NC) | Não, sem autorização extra | Depende das demais cláusulas |

Na dúvida sobre o canal ("o livro é gratuito, mas serve para vender um curso"), trate como uso comercial ou peça orientação à pessoa responsável.

## Reconciliação rápida

Para listar as imagens usadas pelos capítulos, com o caminho completo a partir da raiz do livro:

```bash
for f in capitulos/*/CHAPTER.md; do
  d=$(dirname "$f")
  grep -oE '!\[[^]]*\]\([^) ]+' "$f" | sed -E "s|.*\]\(|$d/|"
done | sort -u
```

Compare a lista com a primeira coluna do registro. Acrescente `files.cover` e `files.logo`, e repita para os arquivos de `editorial/` se algum deles tiver imagem.

---
name: ebookfy-01-organizar
description: Prepara um livro novo ou organiza uma pasta existente. Use para localizar a ficha, separar fontes das saídas e conferir o projeto antes de planejar capítulos.
---

# Organizar o projeto

Comece pelo diretório indicado pelo autor. Localize o ebook.toml mais próximo e leia as tabelas book, files, chapters e output. Em um repositório vazio, execute `ebookfy init`. Quando já houver material, examine a árvore antes de mover arquivos e use a etapa 15 para importar um manuscrito.

Descreva o leitor, o que ele já sabe e a tarefa que deverá conseguir terminar. Use essa descrição para preencher a ficha. Combine a grafia do título e da autoria com quem assina. Mantenha anotações de trabalho fora da lista de capítulos. Registre dúvidas factuais para a etapa 02.

Execute `ebookfy info --json` a partir de uma pasta de capítulo. Compare o título, o idioma, a versão da obra e a ordem de leitura com a edição pretendida. Se a consulta abrir outro livro, confira a posição do TOML antes de editar.

## Referência de trabalho

Consulte [Mapa do projeto e da ficha](references/mapa-do-projeto.md) para escolher o destino de cada material.

## Checklist da entrega

- [ ] O título consultado identifica o livro solicitado.
- [ ] Cada caminho em files leva ao material editorial correspondente.
- [ ] O resumo do projeto nomeia o leitor, sua tarefa e a primeira lacuna a pesquisar.

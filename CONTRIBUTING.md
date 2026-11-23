# Contribuindo com o Ebookfy Starter Kit

Use o [Discord da Promovaweb](https://promovaweb.com/discord) para discutir uma alteração no modelo. Mantenha a pasta do capítulo e sua entrada no TOML juntas.

## Validar o modelo

Rode `ebookfy info --json` e `ebookfy build` na raiz. Abra as três saídas e confira a imagem do capítulo. As instruções das skills vivem no [framework](https://github.com/promovaweb/ebookfy). Atualize a instalação com `npx skills add promovaweb/ebookfy -a universal -a claude-code -a codex -a opencode -y` e confira o arquivo `skills-lock.json`.

Atualize a versão do template em `VERSION` e o changelog antes do commit, tag e GitHub Release. Cada livro derivado controla a edição do manuscrito em `ebook.toml`.

# Contribuindo com o Ebookfy Starter Kit

Converse pelo [Discord da Promovaweb](https://promovaweb.com/discord) ou numa [issue](https://github.com/promovaweb/ebookfy-starter-kit/issues) antes de uma alteração grande no modelo. Mantenha a pasta do capítulo e sua entrada no TOML juntas.

## Validar o modelo

Rode `ebookfy doctor`, `ebookfy info --json` e `ebookfy build` na raiz. Abra as três saídas e confira a figura, a tabela, a nota de rodapé e os links entre capítulos. O livro de exemplo é o mesmo da raiz do framework: altere-o primeiro lá e copie `capitulos/`, `editorial/`, `notas/` e `ebook.toml` para cá. As instruções das skills vivem no [framework](https://github.com/promovaweb/ebookfy). Atualize a instalação com `npx skills add promovaweb/ebookfy -a universal -a claude-code -a codex -a opencode -y` e confira o arquivo `skills-lock.json`.

Atualize a versão do template em `VERSION` e o changelog antes do commit, tag e GitHub Release. Cada livro derivado controla a edição do manuscrito em `ebook.toml`.

## Licença

As contribuições entram sob a mesma licença do modelo, a [MIT](LICENSE). As skills instaladas em `.agents/skills/` vêm do [Ebookfy](https://github.com/promovaweb/ebookfy) e seguem a GNU AGPL 3.0 de lá.

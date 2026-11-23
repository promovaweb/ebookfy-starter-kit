---
name: ebookfy-14-distribuir
description: Prepara a entrega da edição aprovada e confere a cópia que o leitor recebe. Use depois da exportação para relacionar os arquivos, calcular SHA-256, enviar ao destino autorizado e baixar de volta para comparar. Também serve para trocar uma edição já distribuída sem confundir versões. Registra tudo em notas/entrega.md.
---

# Distribuir a edição

Esta etapa leva os exemplares conferidos até o leitor e confirma que o arquivo que ele baixa é o mesmo que foi aprovado. Erros de distribuição são comuns e silenciosos: arquivo da edição anterior no link, cache servindo versão antiga, permissão errada num link privado.

## Quando usar

- Depois da etapa 13, com a prova registrada e sem achado `impede` aberto.
- Para substituir uma edição distribuída por uma nova versão.
- Quando um leitor relata que recebeu arquivo errado, corrompido ou sem acesso.

Envio para um destino só acontece com autorização expressa da pessoa responsável. Se o pedido for apenas preparar, entregue os arquivos e o registro, sem enviar.

## Antes de começar

1. Confira em `notas/entrega.md` a prova da etapa 13 para esta versão.
2. Confirme com a pessoa responsável: destino (área de membros, loja, link privado, repositório), quem tem acesso, se a edição anterior continua disponível.
3. Leia `book.version`, `book.rights` e `output.formats`.

## Procedimento

1. **Parta da lista do build conferido.** Use `notas/build.json`, gravado na etapa 13 com a saída do build que passou pela prova. Não recompile: o MOBI muda a cada build, e uma troca de versão do Pandoc ou do WeasyPrint também muda o PDF e o EPUB; os exemplares deixariam de ser os conferidos. Não pegue arquivos soltos da pasta de saída: ela pode ter edições anteriores.
2. **Relacione os exemplares** no formato da [conferência da entrega](references/conferencia-da-entrega.md): formato, caminho, tamanho e SHA-256.
3. **Confira a identificação.** Versão no nome do arquivo e na capa do PDF. No EPUB, título, identificador, direitos e data nos metadados; a versão só aparece se a arte da capa digital a mostrar. `book.rights` adequado ao canal (público, alunos, clientes).
4. **Envie, se autorizado.** Transfira os arquivos ao destino. Mantenha o nome `<slug>-v<version>.<formato>`, que deixa a versão visível para o leitor.
5. **Baixe de volta como o leitor.** Use o mesmo caminho de acesso do leitor: link público, conta de aluno, área de membros. Em material privado, teste com uma conta que tenha exatamente o acesso esperado e com uma que não deveria ter.
6. **Compare.** Calcule o SHA-256 da cópia baixada e compare com o local. Abra a cópia baixada e confira a versão pelo nome do arquivo e pela capa do PDF.
7. **Registre** em `notas/entrega.md`: destino, links, data, hashes conferidos e quem testou o acesso.
8. **Trate a edição anterior** conforme o combinado: substituída, mantida com aviso ou arquivada. Use o [guia de versões](references/versoes-e-substituicao.md) para escolher a nova versão e avisar quem já tinha a anterior.

## Regras do Ebookfy que afetam esta etapa

- O nome do arquivo é `<slug>-v<version>.<formato>`. Mesma versão compilada de novo gera o mesmo nome com conteúdo possivelmente diferente; por isso a versão muda a cada edição distribuída.
- A pasta de saída acumula as versões compiladas. O `notas/build.json` da etapa 13 é a fonte dos arquivos da entrega.
- `book.rights` e `book.identifier` vão para os metadados do EPUB e acompanham o arquivo para onde ele for.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| Hash da cópia baixada difere do local. | Arquivo errado enviado, upload incompleto ou recompressão no destino. | Reenvie a partir da lista do build e compare de novo. Se o destino recomprime, registre isso e confira abrindo o arquivo. |
| Leitor recebe a edição antiga. | Cache do destino ou link apontando para o arquivo anterior. | Use nome com versão nova; limpe o cache ou troque o link. |
| Link privado abre para qualquer pessoa. | Permissão de compartilhamento ampla. | Corrija a permissão e teste com uma conta sem acesso. |
| Duas versões com o mesmo número circulando. | Recompilação da mesma versão depois de distribuir. | Publique como nova versão e avise. |
| EPUB recusado pela loja. | Metadados incompletos ou identificador inválido para o canal. | Confira as exigências do canal e ajuste `[book]`. |

## Entrega

- Exemplares no destino autorizado, ou preparados para envio quando o pedido for só preparar.
- `notas/entrega.md` com a relação de arquivos, hashes, destino, links e testes de acesso.
- Tratamento da edição anterior registrado e comunicado.

## Checklist da entrega

Preparação (sempre):

- [ ] Os arquivos vêm de `notas/build.json`, o build que passou pela prova da etapa 13.
- [ ] A prova da etapa 13 para esta versão está registrada.
- [ ] Cada exemplar tem formato, caminho, tamanho e SHA-256 registrados.
- [ ] A versão no nome do arquivo e na capa do PDF coincide com `book.version`.

Envio (quando autorizado):

- [ ] O envio teve autorização expressa da pessoa responsável.
- [ ] A cópia foi baixada pelo mesmo caminho do leitor e o hash bate com o local; se o destino altera o arquivo, isso está registrado e a cópia foi aberta e conferida.
- [ ] Em material privado, o acesso foi testado com uma conta autorizada e com uma não autorizada.
- [ ] Links e data de publicação estão em `notas/entrega.md`.
- [ ] A edição anterior foi tratada conforme o combinado.

## Referências

- [Conferência da entrega](references/conferencia-da-entrega.md): comandos de hash e modelo de registro.
- [Versões e substituição](references/versoes-e-substituicao.md): como numerar edições e trocar uma edição já distribuída.

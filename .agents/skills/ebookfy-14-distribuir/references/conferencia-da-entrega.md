# Conferência da cópia distribuída

Calcule o SHA-256 de um arquivo local com Node.js; substitua o último argumento pelo caminho informado pelo build:

```sh
node -e "const fs=require('node:fs'), h=require('node:crypto').createHash('sha256');fs.createReadStream(process.argv[1]).on('data',b=>h.update(b)).on('end',()=>console.log(h.digest('hex')))" ebook/oficina-v1.2.0.epub
```

Repita com o arquivo baixado. Mesmo nome e tamanho ajudam a reconhecer o exemplar, mas os dois hashes permitem comparar os bytes. Para uma pasta compartilhada, confira também se o link aponta ao arquivo e se a pessoa com o acesso esperado consegue baixá-lo.

Uma linha por exemplar pode guardar edição, formato, nome do arquivo, tamanho, SHA-256 e destino conferido. Registre separadamente “preparado”, “enviado” e “cópia recuperada” conforme o que realmente ocorreu.

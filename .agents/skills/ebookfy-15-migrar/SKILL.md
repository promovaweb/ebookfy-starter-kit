---
name: ebookfy-15-migrar
description: Migra um manuscrito único ou uma coleção de capítulos para Ebookfy. Use como entrada para um acervo existente, preservando leitura, ativos locais e rastreabilidade.
---

# Migrar um livro existente

Trabalhe numa cópia e guarde a edição de origem para comparação. Procure a ordem declarada pelo projeto, como reading-order.txt ou sumário editorial. Em um manuscrito único, identifique os títulos que delimitam unidades de leitura; preserve blocos de código, notas e legendas durante a divisão.

Mapeie origem, destino e posição de cada trecho antes de mover arquivos. Separe prefácio, créditos e autoria em files. Transfira os capítulos para pastas com CHAPTER.md e imagens locais. Atualize links relativos, âncoras e notas que atravessavam os limites antigos. Preserve pesquisa e rascunhos fora da leitura publicada.

Monte o TOML e execute `ebookfy info`. Compare o primeiro, o último e os capítulos intermediários com o mapa. Compile os formatos previstos, confira a sequência e registre lacunas, duplicações corrigidas e trechos que precisam de revisão editorial.

## Referência de trabalho

Consulte [Mapa de migração e reconciliação](references/mapa-de-migracao.md) para mapear uma origem e recuperar uma figura após a divisão.

## Checklist da entrega

- [ ] Todo trecho publicado possui destino identificado ou exclusão explicada.
- [ ] A sequência nova foi comparada com o sumário ou a edição anterior.
- [ ] Figuras, notas, citações e links internos funcionam nos novos limites dos capítulos.

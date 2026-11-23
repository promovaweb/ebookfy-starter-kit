---
name: ebookfy-02-pesquisar
description: Apura afirmações, comandos, números e imagens antes da redação de um capítulo ou quando uma passagem é contestada. Use para rastrear cada afirmação até a fonte mais próxima do fato, reproduzir comandos e registrar a procedência em notas/fontes.md.
---

# Pesquisar e registrar as fontes

Esta etapa transforma o que o livro pretende afirmar em registros conferidos. Cada afirmação que o leitor pode querer verificar ganha uma fonte localizável, uma data de consulta e a passagem exata usada. Comandos e procedimentos são reproduzidos, não copiados de memória.

## Quando usar

- Antes de redigir um capítulo, para reunir o material das perguntas listadas no sumário.
- Quando uma revisão marca uma afirmação sem fonte ou uma passagem contestada.
- Quando a ferramenta, a versão ou a regra que o livro descreve mudou depois da redação.
- Quando chega uma imagem, tabela ou citação de terceiro que vai entrar na edição.

Passe para a etapa 03 quando as perguntas de cada capítulo tiverem fonte ou pendência declarada. Passe para a etapa 04 quando o capítulo da vez estiver apurado. Materiais de terceiros seguem também para a etapa 09.

## Antes de começar

1. Leia `notas/briefing.md` para saber leitor, escopo e pendências já levantadas.
2. Leia `notas/sumario.md`, quando existir, para saber a pergunta de cada capítulo.
3. Abra ou crie `notas/fontes.md` no formato da [ficha de apuração](references/ficha-de-apuracao.md).

## Procedimento

1. **Liste as afirmações.** Para o capítulo da vez, escreva cada afirmação verificável como uma frase completa: "O Schedule Trigger usa o fuso horário configurado na instância". Perguntas vagas ("como funciona o agendamento?") viram uma ou mais afirmações conferíveis.
2. **Escolha a fonte mais próxima do fato.** Siga a ordem do [guia de fontes](references/guia-de-fontes.md): o próprio sistema em execução, a documentação ou o código oficial da versão citada, o texto normativo, a publicação original, o relato de quem viveu o fato. Blogs, fóruns e resumos servem para achar a fonte original, não para substituí-la.
3. **Leia no contexto.** Confira a seção inteira, a data de publicação, a versão a que o texto se refere e se há ressalvas logo abaixo do trecho.
4. **Reproduza o que for executável.** Para comandos, configurações e telas, execute no ambiente descrito no livro. Registre versão do programa, sistema, comando exato, entrada e a saída observada. Se a saída mudou em relação ao rascunho, a fonte é a saída nova.
5. **Registre na ficha.** Uma entrada por afirmação: frase, fonte com título e endereço, data de consulta, trecho usado, capítulo de destino e situação (`confirmada`, `ajustada`, `pendente`).
6. **Resolva divergências.** Quando duas fontes discordam, compare data, versão e escopo. Se ainda divergirem, escreva a afirmação com o recorte que as duas sustentam ou leve a pendência à pessoa responsável. Nunca escolha a versão mais conveniente para o texto.
7. **Encaminhe materiais de terceiros.** Imagens, tabelas, diagramas e citações longas vão para `notas/atribuicoes.md` com autor, origem, licença ou autorização e o arquivo do livro que os usa.
8. **Guarde capturas fora da leitura.** Saídas longas, prints de referência e PDFs consultados ficam em `notas/fontes/`, com nome que indique o capítulo. Só a figura que vai para a página segue para `capitulos/<pasta>/imagens/` na etapa 05.

## Regras do Ebookfy que afetam esta etapa

- O compilador lê só os arquivos de `[[chapters]]` e de `[files]`, mais as imagens que eles referenciam. `notas/` pode crescer à vontade sem aparecer no livro, desde que nenhum capítulo aponte para um arquivo dali.
- Uma figura que vai para a página deve morar em `imagens/` do capítulo. O `ebookfy build` recusa imagem com caminho fora do livro ou endereço `https://`: baixe o arquivo de apoio para `notas/fontes/` e a figura final para `imagens/`.
- O livro declara um idioma em `book.language`. Citações em outro idioma entram traduzidas no texto, com o original registrado na ficha.

## Problemas frequentes

| Sintoma | Causa provável | Correção |
| --- | --- | --- |
| A afirmação só aparece em blogs que se citam entre si. | Fonte original não localizada. | Busque a documentação, o código ou o anúncio oficial. Sem isso, marque `pendente` e avise. |
| O comando do rascunho falha ao ser reproduzido. | Versão diferente ou passo omitido. | Registre a versão em uso, refaça o procedimento completo e ajuste a afirmação. |
| A documentação descreve outra versão. | Página antiga ou de versão futura. | Procure a página da versão citada no briefing ou registre a diferença. |
| Número sem data ("mais de 500 integrações"). | Dado que muda com o tempo. | Registre a data da consulta e escreva o número com ela, ou troque por uma formulação estável. |
| Imagem achada em busca sem autor claro. | Procedência desconhecida. | Não use. Procure a origem ou produza uma figura própria. |

## Entrega

- `notas/fontes.md` com uma entrada por afirmação do capítulo, cada uma com situação.
- Capturas e saídas de apoio em `notas/fontes/`.
- `notas/atribuicoes.md` atualizado com os materiais de terceiros.
- Um resumo para a pessoa: quantas afirmações foram confirmadas, quais foram ajustadas e quais seguem pendentes, com o motivo.

## Checklist da entrega

- [ ] Cada afirmação verificável do capítulo tem entrada própria na ficha.
- [ ] Cada fonte tem título, endereço ou localização, data de consulta e trecho usado.
- [ ] Comandos e telas foram reproduzidos, com versão, sistema e saída registrados.
- [ ] Divergências entre fontes estão descritas com a formulação escolhida e o motivo.
- [ ] Números e dados que mudam com o tempo trazem a data da consulta.
- [ ] Nenhuma afirmação se apoia só em resumo, fórum ou texto gerado por IA.
- [ ] Materiais de terceiros estão em `notas/atribuicoes.md` com origem e condição de uso.
- [ ] Pendências estão marcadas e foram comunicadas a quem pode resolvê-las.
- [ ] Nada da pesquisa foi colocado dentro de `capitulos/` sem passar pela etapa 04 ou 05.

## Referências

- [Ficha de apuração](references/ficha-de-apuracao.md): formato de `notas/fontes.md` com entradas preenchidas.
- [Guia de fontes](references/guia-de-fontes.md): ordem de preferência por tipo de afirmação e como lidar com divergência.

# Ficha de apuração

> Os exemplos usam um livro fictício, *Primeiros fluxos no n8n*. Os fatos, versões e trechos citados ilustram o formato do registro e não são apuração real.

Grave em `notas/fontes.md`, agrupada por capítulo. Uma entrada por afirmação. A situação usa três valores: `confirmada` (a fonte sustenta a frase como está), `ajustada` (a frase mudou para caber no que a fonte diz) e `pendente` (falta fonte ou resposta).

## Formato

```markdown
## Capítulo 03 · Agendar a execução

### F-03-01 · confirmada
- Afirmação: O Schedule Trigger dispara conforme o fuso horário definido nas configurações do workflow; sem isso, usa o fuso da instância.
- Fonte: Documentação do n8n, "Schedule Trigger node", seção "Timezone". https://docs.n8n.io/...
- Consulta: 2026-11-20, documentação da versão 2.3.
- Trecho usado: "The node uses the workflow timezone if set, otherwise the instance timezone."
- Reprodução: instância local 2.3.1 em Docker, TZ da instância America/Sao_Paulo, workflow sem fuso. Disparo agendado às 09:00 rodou às 09:00 de Brasília.
- Destino: capitulos/03-agendar/CHAPTER.md, seção "Se a execução sair no horário errado".
```

## Exemplos de cada situação

```markdown
### F-06-01 · ajustada
- Afirmação original: O n8n reexecuta automaticamente um workflow que falhou.
- Afirmação ajustada: Cada node pode repetir a própria execução com "Retry On Fail"; o workflow inteiro não é reexecutado sozinho.
- Fonte: Documentação do n8n, "Node settings", item "Retry On Fail". Consulta 2026-11-20.
- Reprodução: node HTTP Request apontado para endereço inexistente, Retry On Fail com 3 tentativas. O log mostra 3 tentativas e o workflow para com erro.
- Destino: capitulos/06-erros/CHAPTER.md.

### F-01-05 · pendente
- Afirmação: A versão em nuvem limita execuções por mês no plano inicial.
- Motivo: a página de preços mudou duas vezes em novembro e não traz o número do plano inicial.
- Próximo passo: perguntar à Ana se o livro deve citar planos ou remover a afirmação.
- Destino: capitulos/01-instalar/CHAPTER.md.
```

## Registro de comando reproduzido

Quando a afirmação depende de uma execução, guarde a saída completa em `notas/fontes/` e cite o arquivo na entrada.

```markdown
- Reprodução: `docker compose up -d` com o compose do capítulo 01, Docker 27.3, Debian 13.
  Saída em notas/fontes/01-docker-compose-up.txt. O container n8n ficou "healthy" em 40 s.
```

## Revisão da ficha antes de redigir

Antes de passar o capítulo para a etapa 04, leia a ficha inteira do capítulo e confira:

- toda afirmação do sumário daquele capítulo aparece na ficha;
- não há entrada `confirmada` sem trecho usado ou sem reprodução;
- as entradas `pendente` têm próximo passo e responsável.

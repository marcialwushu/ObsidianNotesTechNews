---
link: https://github.com/bacen/pix-api/issues/504
author: amarborto
published: 2022-04-23T12:25:00
tags: []
---
# Highlights


---
# Dúvida no erro recebido de GET /cobv
Olá estou alterando de instuição bancaria e me deparei com esse erro no GET de cobv que não existia anteriormente, o padrão de data esta correto até onde entendo, não importa o quando eu altero o intervalo de busca sempre aparece esse erro. Conseguem ver algo errado?

```

/cobv?inicio=2022-04-01T00:00:00Z&fim=2022-04-30T23:59:59Z&cpf=DOC_VALIDO_AQUI&paginacao.paginaAtual=0&paginacao.itensPorPagina=100

{
   httpStatus: 400,
   status: 400,
   type: 'https://pix.bcb.gov.br/api/v2/error/RequisicaoInvalida',
   title: 'Requisição inválida',
   correlationId: 'service-084ce088-9b1f-4c01-8479-375d076d7fe3',
   violacoes: [
     {
       propriedade: '.query.fim',
       razao: 'O timestamp representado pelo parâmetro fim é inválido',
      valor:  [ '2022-04-30T23:59:59Z', '2022-04-30T23:59:59Z' ]
    }
   ]
 }
```
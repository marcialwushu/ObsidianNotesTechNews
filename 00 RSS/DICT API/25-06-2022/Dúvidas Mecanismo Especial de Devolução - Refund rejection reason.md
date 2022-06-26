---
link: https://github.com/bacen/pix-dict-api/issues/36
author: amandachermont
published: 2021-10-29T14:54:00
tags: []
---
# Highlights


---
# Dúvidas Mecanismo Especial de Devolução - Refund rejection reason
Pessoal, bom dia.

De acordo com o Manual Operacional do DICT, existem três motivos para rejeição de pedidos de devolução que podem ser utilizados, sendo eles:

-   no_balance : falta de saldo na conta do cliente
-   account_closure : relacionamento com cliente encerrado
-   cannot_refund : participante não pode acionar Mecanismo Especial de Devolução

Temos dúvidas com relação a qual motivo de rejeição utilizar nos seguintes cenários:

1.  Conta do cliente bloqueada (não podemos retirar o dinheiro da conta para fazer a devolução, ex: bacenjud ou bloqueio cautelar em andamento)
2.  Devolução já foi feita manualmente pelo cliente
3.  Instabilidade no Pix
4.  Pedido de devolução inválido (ex: duplicado, transação +90 dias, pedido tipo fraude sem infração aprovada, etc)

Poderiam por favor nos auxiliar?
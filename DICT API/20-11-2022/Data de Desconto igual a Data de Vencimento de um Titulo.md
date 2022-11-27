---
link: https://github.com/bacen/pix-api/issues/481
author: rgonzagaAut
published: 2022-01-05T19:22:00
tags: []
---
# Highlights


---
# Data de Desconto igual a Data de Vencimento de um Titulo
Tenho uma dúvida acerca da Data de Desconto: no PUT/PATCH cobv, é colocado que a data de desconto deve ser obrigatoriamente menor que a data de vencimento do título. Temos vários casos de cobrança onde esta data pode ser igual a data de vencimento, mas nunca maior que a data de vencimento ( Ou seja, não se deve dar desconto a um título vencido ).

Tenho exemplos de títulos/boletos que são emitidos por escolas, por exemplo. A API PIX deve recusar cobrança cuja a data de desconto seja igual a data de vencimento do título?
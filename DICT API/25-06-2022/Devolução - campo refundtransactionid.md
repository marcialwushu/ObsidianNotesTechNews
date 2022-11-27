---
link: https://github.com/bacen/pix-dict-api/issues/45
author: amandachermont
published: 2021-12-03T17:49:00
tags: []
---
# Highlights


---
# Devolução - campo refundtransactionid
Prezados, boa tarde. Revisando a documentação da API DICT, identificamos que o campo refundtransactionid não é de preenchimento obrigatório ("required") ao fechar uma solicitação de devolução no MED. Em testes realizados em homologação, alguns PSPs estão enviando esse campo em branco ao concluir uma devolução.

Gostaríamos de sugerir de alterar este campo para "required" de forma condicional: quando for encerramento de um devolução em que houve a refund-transaction, esse campo deve ser obrigatório.

Isso ajuda a ter mais confiança no mecanismo, possibilitando que possamos fazer conciliação entre a solicitação de refund e o refund efetivamente criado.
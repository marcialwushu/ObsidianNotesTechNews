---
link: https://github.com/bacen/pix-api/issues/483
author: GustavoSTZ
published: 2022-01-06T11:01:00
tags: []
---
# Highlights


---
# [Dúvidas Lote COBV] Validação de Schema
Estamos desenvolvendo os endpoints de lote cobv e surgiu algumas dúvidas:

1 - A violação abaixo se refere que devemos bloquear todas as requisições que tiverem objetos com patterns diferentes, por exemplo, quando vier um txid fora do pattern especificado (exemplo, maior que 35) devemos jogar um erro 400 e bloquear todas as Cobsv recebidas no array? Ou somente bloquear aquela que está com o pattern errado, mudando o status da mesma para NEGADA e permitindo as demais serem processadas?

```
Violações para os endpoints PUT|PATCH /lotecobv/{id}: 
O objeto loteCobV.cobsV não respeita o schema.
```

2 - Questões de segurança, podemos bloquear tal requisição que contém um payload malicioso já na entrada ou precisamos retornar no escopo do GET que foi recusada por conter um payload malicioso? Pergunto isso, pois teríamos que salvar tal payload malicioso para retornar que ele foi negado, o que poderia gerar grandes vulnerabilidades.
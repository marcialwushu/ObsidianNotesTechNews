---
link: https://github.com/bacen/pix-api/issues/506
author: tvps20
published: 2022-05-10T15:56:00
tags: []
---
# Highlights


---
# [Duvida] - Campos obrigatórios no fluxo de Path da Cobv
Na parte de Gerenciamento de cobranças com vencimento, no enpoint de "Revisar cobrança com vencimento" temos a seguinte situação:

![image](https://user-images.githubusercontent.com/23269934/167647007-0fd5d216-f75e-47a9-b6a8-5825c5a88fb1.png)

É possível notar que para realizar o PATCH das informações da cobrança existem campos **required** e também com valores **default** e me deixou em dúvida quanto ao comportamento da atualização de cobranças com vencimentos.

Dados esses pontos e seguindo o exemplo da imagem, para atualizar o campo 'validadeAposVencimento' sou obrigado a passar o campo 'dataDeVencimento' já que o mesmo se encontra como **required**? Outra questão seria com relação a esse valor **default**, se vou atualizar por exemplo o campo 'validadeAposVencimento' passando um valor 'null' explicitamente a api deve considerar o valor **default**? Faço tais questionamentos, pelo fato do PATCH ter como caracteristica o partial update, ou seja, não entendo o porquê da obrigatoriedade de qualquer campo no endpoint, pois na minha visão, por exemplo, se eu quisesse atualizar a validadeAposVencimento eu simplesmente passaria:

`{ "calendario":{ "validadeAposVencimento": 123 } }`
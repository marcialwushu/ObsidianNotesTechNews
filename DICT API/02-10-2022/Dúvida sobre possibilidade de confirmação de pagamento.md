---
link: https://github.com/bacen/pix-api/issues/490
author: JoaoPedroAssis
published: 2022-01-21T11:35:00
tags: []
---
# Highlights


---
# Dúvida sobre possibilidade de confirmação de pagamento
Olá! Tenho uma dúvida que pode ser um pouco básica, mas vamos lá:

Estou com uma dúvida sobre como posso usar (ou se é possível) a API para fazer apenas a confirmação de pagamentos pix. Então a partir de uma chave, saber se os pagamentos estão chegando para ela. O uso seria para o seguinte cenário:

> Um usuário que não possui acesso à conta que vai receber o pix precisa realizar uma cobrança. Ao invés de depender apenas do comprovante gerado pelo pagador, a API forneceria informações necessárias para que eu possa validar ao cobrador que o pix foi bem sucedido.

Basicamente o sistema geraria um QrCode de pagamento e conseguiria validar que o pagamento foi feito. Seria necessário consultar a api de cada um dos PSPs (banco) ou a própria API pix suporta essa funcionalidade?

Lendo as issues, uma possível solução seria a proposta [aqui](https://github.com/bacen/pix-api/issues/482#issuecomment-1006479506), onde o próprio sistema receberia o dinheiro e o transferiria para a conta destido, pegando a confirmação nessa etapa. Queria ver se existe alguma solução diferente, pois não queremos intermediar o fluxo do dinheiro na operação.

Agradeço desde já!
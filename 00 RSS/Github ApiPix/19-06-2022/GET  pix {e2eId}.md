---
link: https://github.com/bacen/pix-api/issues/476
author: eduardomazolini
published: 2021-12-06T15:56:00
tags: []
---
# Highlights


---
# GET /pix/{e2eId}
Estou integrando com um grande banco e o mesmo informou que a API não funciona para listar de PIX por chave ou estático. Existe uma regra/norma que os obrigue a oferecer as funcionalidades desta API sem estas restrições? Meu problema é que recebo webhook de PIX estático com txID (identificando meu ponto recebedor) em seguida tenho que ficar fazendo busca por filtro em vez de ir direto ao e2eid para completar a minha identificação do pagamento.
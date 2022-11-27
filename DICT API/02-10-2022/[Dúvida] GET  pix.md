---
link: https://github.com/bacen/pix-api/issues/522
author: eduoct
published: 2022-08-22T19:02:00
tags: []
---
# Highlights


---
# [Dúvida] GET /pix
Boa tarde,

Tenho um cliente que atende mais de 10 milhões de usuários, onde implementamos a API Pix. Geramos o cob/cobv identificado pelo txid, quando somos notificados do pagamento pelo webhook o ERP dá a baixa na cobrança desse cliente. Até ai tudo ok. Porém, desse montante de 10 milhões, muito deles iniciam o Pix de maneira direta via chave pix (CNPJ ou aleatória, pois já foram informados dessa chave algum dia). Nesse caso, não temos txid e não recebemos o retorno do webhook. Temos desenvolvido uma inteligência de identificação da cobrança pelo GET /pix, onde até então voltava as infos de CPF/CNPJ. Um dos PSPs não volta essa informação, o que me trouxe pra cá, e vi que foi alterada a especificação do GET /pix. Olhei a discussão #153 , mas ainda não entendi como resolver meu problema. Vi que foram incluídos os filtros CNPJ/CPF no GET /pix. Mas temos mais de 3 milhões de cobranças em aberto por CPF/CNPJ aguardando pagamento, teria que minha aplicação realizar essas 3 milhões de consultas e verificar se volta e2eid? Está correto meu entendimento ou existe outra maneira? Obrigado.
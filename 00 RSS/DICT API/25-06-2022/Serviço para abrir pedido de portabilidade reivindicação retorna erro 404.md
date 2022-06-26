---
link: https://github.com/bacen/pix-dict-api/issues/13
author: monise
published: 2020-11-09T10:53:00
tags: []
---
# Highlights


---
# Serviço para abrir pedido de portabilidade/reivindicação retorna erro 404
Olá!! No serviço para abrir um pedido de portabilidade/reivindicação, pode ser retornado o status de erro **404**? Pelo Redoc, os erros mapeados são os abaixo.

![image](https://user-images.githubusercontent.com/5355541/98549540-ae901f00-2279-11eb-9864-8f9a328832ae.png)

Mas estamos recebendo um response com o erro **404**.

`<ds:X509SerialNumber>66906355272994040667436154809</ds:X509SerialNumber></ds:X509IssuerSerial></ds:X509Data></ds:KeyInfo></ds:Signature><type>https://dict.pi.rsfn.net.br/api/v1/error/ClaimKeyNotFound</type><title>Not Found</title><status>404</status><detail>Entry associated with given key does not exist</detail><correlationId>f9d73c535297bc3a1d720d797e6fc10c</correlationId></problem>`
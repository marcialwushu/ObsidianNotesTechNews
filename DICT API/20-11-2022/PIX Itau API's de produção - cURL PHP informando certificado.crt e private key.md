---
link: https://github.com/bacen/pix-api/issues/531
author: EduardoDosSantosPereira
published: 2022-10-24T12:51:00
tags: []
---
# Highlights


---
# PIX Itau API's de produção - cURL PHP informando certificado.crt e private key
Boa tarde.

Estou realizando a integração Recebimentos PIX no Itau. Já possuo o client_id e o client_secret e estou realizando a chamada das API's de produção (api/oauth/token e pix_recebimentos/v2/cob).

Ao consumir a api/oauth/token via POSTMAN informando os arquivos certificado.crt e private key eu obtenho sucesso. Porém ao realizar via cURL no PHP eu obtenho o seguinte retorno de HTTP/1.1 401 Unauthorized:

{ "message" : "Falha ao Extrair TokenInfo filter failed" }

Alguem que realizou essa integração junto ao Itau sabe como posso resolver isso?

Obrigado!
---
link: https://github.com/bacen/pix-api/issues/503
author: amarborto
published: 2022-04-16T12:17:00
tags: []
---
# Highlights


---
# Erro na tentativa de efetuar uma requisição na api do banco: SSL_connect: SSL_ERROR_SYSCALL
Olá, alguém já passou por esse problema onde tentou requisitar algo da api pix do seu banco e ocorreu o seguinte erro do OpenSSL?

```
#Request
curl  -v --tls-max 1.2 --key minha.key --cert meucert.crt -X POST 'endponint.do.banco' --header 'Content-Type: application/x-www-form-urlencoded' --data-urlencode 'grant_type=client_credentials' --data-urlencode 'client_id=credencial' --data-urlencode 'client_secret=credencial' --data-urlencode 'scope=cob.read'

#Resposta
* TLSv1.2 (OUT), TLS handshake, Client hello (1):
* OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to ...:443
* Closing connection 0
```

Esse Endpoint em questão é o de produção, já no de homologação funciona 100% e no mesmo servidor; Essa requisição foi feita no CURL para eliminar a possibilidade do problema ser na aplicação em si, feito tanto com credenciais e endpoint de homologação (que funciona e retorna o resultado esperado) e também com credenciais e endpoint de produção (que ocorre o erro em questão)
---
link: https://github.com/bacen/pix-dict-api/issues/46
author: rafaelchagasb
published: 2021-12-28T16:28:00
tags: []
---
# Highlights


---
# Falta do header cache-control/max-age no CheckKeys
Segundo o Manual Operacional do Dict na seção **17. Cache de existência de chave Pix**:

O cache de existência de chave Pix pode ser alimentado a partir das seguintes fontes:

> d. verificação de chaves registradas no DICT (checkKeys).

Caso o registro no cache seja feito por meio da fonte “d”, o registro deve seguir as diretivas contidas no header Cache-Control, para que ele seja válido.

Porém ao chamar o **endpoint /keys/check** não está sendo retornado o atributo **max-age** no header **cache-control**.
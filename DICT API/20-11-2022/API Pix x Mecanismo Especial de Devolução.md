---
link: https://github.com/bacen/pix-api/issues/450
author: rubenskuhl
published: 2021-09-18T09:44:00
tags: []
---
# Highlights


---
# API Pix x Mecanismo Especial de Devolução
Digamos que 3 hipóteses se apliquem:

-   Um Pix havia sido sinalizado via API por ter txid (quer seja estático ou dinâmico)
-   O PSP Recebedor aderiu ao Mecanismo Especial de Devolução
-   O EC Recebedor aderiu ao Mecanismo Especial de Devolução

Como fica a sinalização via API, tanto de webhook quanto de GET em /pix, disso ? Lembrando que há casos finais (os de falha sistêmica) e casos de análise (fraude) onde há primeiro um congelamento do recurso e depois uma liberação ou definição.
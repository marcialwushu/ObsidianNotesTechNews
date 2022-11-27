---
link: https://github.com/bacen/pix-api/issues/437
author: rubenskuhl
published: 2021-08-24T22:26:00
tags: []
---
# Highlights


---
# Idéias para QR-Code do pagador
Seguem alguns pensamentos meus e do @SeanWykes sobre como poderia ser a API Pix para suporte a QR-Code do pagador

```
Rubens Kuhl — Que mudanças na API vocês imaginam para usar o QR-Code do pagador ?
Sean Wykes — Rubens, pelo lado pagador, penso de imediato que será preciso uma forma de subir o QR recebido para encaminhamento para o pagador pelo SPI. Pode ser tão simples quando um PUT o POST /qrcode. Daí, a confirmação do pagamento poderia vir pela notificação do webhook. O que ainda não vi é a questão de TXID, pois se for gerado pelo pagador, como identificar o pagamento na notificação?

Já para atender o lado pagador, a coisa complica devida às diferentes regras e funcionalidades propostas
Rubens Kuhl — Possivelmente o POST do /qrcode retorne o txid. O problema é garantir idempotência. O que me ocorre é o QR-Code ter um PaymentID do pagador cujo objetivo seja apenas esse de idempotência, não de conciliação. Então se fizer o POST do mesmo QR-Code duas vezes, retorna o mesmo TXID.
Sean Wykes — Aí fica bacana. Como o QR pagador é completamente diferente do QR PIX atual, não precisa nem ter um TXID, então este pode ser gerado pelo recebedor ou seu PSP, e o PSP recebedor manter a relação entre os dois (PaymentID, TXID). Ao chegar no PSP pagador, será disparado o pagamento com o TXID do recebedor normalmente, assim funcionando o webhook e as consultas, inclusive um GET /qrcode/{txid} etc
```
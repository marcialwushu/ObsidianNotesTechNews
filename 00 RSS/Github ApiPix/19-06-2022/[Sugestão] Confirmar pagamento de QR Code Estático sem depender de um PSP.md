---
link: https://github.com/bacen/pix-api/issues/508
author: josimarcordeiro
published: 2022-05-28T15:10:00
tags: []
---
# Highlights


---
# [Sugestão] Confirmar pagamento de QR Code Estático sem depender de um PSP
Muitas instituições financeiras ainda não disponibilizaram API PIX para seus clientes. Tenho dúvidas se algumas delas realmente querem disponibilizar ou se querem forçar seus clientes a utilizar outras soluções que seriam mais rentáveis (por exemplo, PIX na maquinha de cartão com cobrança de um % sobre a transação).

O Banco Central deveria criar uma forma do usuário recebedor realizar sua conciliação bancária via API sem depender de um PSP.

Exemplo: Cliente recebedor utiliza sua chave PIX para criar um QR Code estático com um txId único. O Banco central disponibiliza uma consulta via API diretamente sua base ([https://br.gov.bcb.pix](https://br.gov.bcb.pix)) onde o cliente recebedor irá informar na requisição a chave PIX e o txId e o BC irá retornar apenas "true" ou "false" para essa consulta. Uma solução desse tipo iria permitir o desenvolvimento de Softwares de conciliação bancária mais fáceis dos usuários (recebedores) utilizar pois esses usuários não iriam depender de credenciais fornecidas por um PSP.

O fato é que o Banco Central não pode deixar os clientes reféns dos PSP's para funcionalidades básicas.
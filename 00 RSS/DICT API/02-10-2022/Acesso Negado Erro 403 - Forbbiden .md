---
link: https://github.com/bacen/pix-api/issues/519
author: lucas-fsousa
published: 2022-07-30T14:52:00
tags: []
---
# Highlights


---
# Acesso Negado Erro 403 - Forbbiden 
Estou tentando fazer uma requisição para o endpoint de criação do webhook, porém só recebo a seguinte mensagem de erro: { "type": "[https://pix.bcb.gov.br/api/v2/error/AcessoNegado](https://pix.bcb.gov.br/api/v2/error/AcessoNegado)", "title": "Acesso Negado", "status": 403, "detail": "Requisição de participante autenticado que viola alguma regra de autorização." }

Os certificados estão ok e o corpo da requisição é:

{ "webhookUrl": "[https://pixviewerapi-desenv.azurewebsites.net/PixViewerTest/api/v1/post](https://pixviewerapi-desenv.azurewebsites.net/PixViewerTest/api/v1/post)" }

Gostaria de saber quais são os principais causadores dessa violação de regras por que não encontrei essa info na API [https://bacen.github.io/pix-api/#/Webhook/put_webhook__chave_](https://bacen.github.io/pix-api/#/Webhook/put_webhook__chave_)
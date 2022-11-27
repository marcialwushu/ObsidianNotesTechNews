---
link: https://github.com/bacen/pix-api/issues/523
author: rudineirk
published: 2022-08-23T11:44:00
tags: []
---
# Highlights


---
# [Dúvida] Expiração cobrança com vencimento (COBV)
Tenho uma dúvida sobre a expiração dos qrcodes de cobrança com vencimento, parece ter alguma divergência das docs com a implementação dos bancos, pois um qrcode que deveria poder ser liquidado estava dando falha na leitura/liquidação por causa do prazo.

Segue o caso:

```
{
  "calendario": {
    "dataDeVencimento": "2022-08-18",
    "validadeAposVencimento": 2
  },
  ...
}
```

tentando fazer o pagamento desse qrcode na segunda (22/08), ocorreu a seguinte situação nos bancos:

-   Nubank: Conseguia ler o qrcode mas dava erro na liquidação
-   Santander: Conseguia ler o qrcode mas dava erro na liquidação
-   Inter: Erro de qrcode inválido na leitura
-   Bradesco: Erro de qrcode inválido na leitura
-   Caixa: Erro "Documento fora do prazo de pagamento" na liquidação do pagamento

pelo que está descrito nessa seção das docs de criação do COBV, deveria ser possível realizar o pagamento desse qrcode: ![Screenshot from 2022-08-22 15-30-29](https://user-images.githubusercontent.com/5260987/186187365-adde4789-01e8-4d48-870a-d68b3c590a5b.png) ![Screenshot from 2022-08-23 11-43-23](https://user-images.githubusercontent.com/5260987/186188188-bd823923-af40-44e8-9330-8a9fbf18b774.png)

A expiração dele seria no sábado (20/08), mas como não é dia útil deveria passar para segunda (22/08). Qual é o comportamento correto nesses casos? O que os bancos estão implementando ou o que está na documentação?
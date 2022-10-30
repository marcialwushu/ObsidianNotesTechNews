---
link: https://github.com/bacen/pix-api/pull/515
author: tarsiswt
published: 2022-07-05T17:19:00
tags: []
---
# Highlights


---
# Remove atributo redundante do schema `CobVGerado`
A propriedade `txid` do atributo em `#/components.schemas.CobVGerada.allOf[3].properties.loc` é desnecessária já que o schema referenciado `PayloadLocation` não contém esse atributo.

Parece ser sido introduzido há algum tempo em [https://github.com/bacen/pix-api/commit/d302e9e4d219d8f94fc934c2e20d0f68c254a2d5](https://github.com/bacen/pix-api/commit/d302e9e4d219d8f94fc934c2e20d0f68c254a2d5).
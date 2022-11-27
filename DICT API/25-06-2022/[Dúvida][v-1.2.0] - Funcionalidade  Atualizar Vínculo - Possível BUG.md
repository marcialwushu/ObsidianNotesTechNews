---
link: https://github.com/bacen/pix-dict-api/issues/23
author: ekiametis
published: 2021-05-06T09:56:00
tags: []
---
# Highlights


---
# [Dúvida][v-1.2.0] - Funcionalidade: Atualizar Vínculo - Possível BUG
Prezados,

Na versão 1.2.0 da API do DICT, é permitido alterar os dados do "Owner" na funcionalidade de Atualizar Vínculo. Porém ao tentar realizar a alteração de uma chave aleatória, só é permitido com a razão "BRANCH_TRANSFER". Não achei em nenhum lugar o motivo para tal regra. Existe alguma documentação para que possa ler e entender melhor a respeito disso?

Não poderia ser usada a razão "USER_REQUESTED" ou "RECONCILIATION", conforme documentado na API?

![image](https://user-images.githubusercontent.com/7198068/117301685-4188cb00-ae51-11eb-8f51-65e8b2d095d6.png)
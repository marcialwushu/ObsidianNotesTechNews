---
link: https://github.com/bacen/pix-api/issues/525
author: pedroluiznogueira
published: 2022-09-12T20:09:00
tags: []
---
# Highlights


---
# [Dúvida] Assinatura da requisição de callback do webhook com private key
Olá,

Estou com uma dúvida sobre a implementação de uma recomendação supostamente feita pelo `bacen` nas requisições de callback do webhook para pix.

Me foi informado que o `bacen` recomenda que a requisição de eventos do webhook enviada pelo PSP seja assinada com as chaves pública e privada do cliente. Isso me parece estranho, visto que geralmente assinamos com a chave privada e a verificação é feita posteriormente com a pública (sem envolvimento da chave pública na assinatura).

1.  Poderiam me informar se o `bacen` realmente recomenda isso e se há alguma documentação para o mesmo ? Não consegui encontrar.
2.  Acredito que sendo feita dessa forma ou apenas com a chave privada conforme mencionei, o `bacen` tenha alguma recomendação de onde deverá ser enviada a assinatura. Existe alguma recomendação de header específico ou algo assim ?

Agradeço pela ajuda. :smile:
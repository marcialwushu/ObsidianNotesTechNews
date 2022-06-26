---
link: https://github.com/bacen/pix-api/issues/509
author: ThainaDhaila
published: 2022-06-01T10:38:00
tags: []
---
# Highlights


---
# NEGÓCIO Caracteres especiais no Campo  InfoAdicional de QR Codes 
Olá! O Manual de Padrões para Iniciação do Pix estabelece que o campo de InfoAdicional é um Conjunto livre de caracteres, com limite de tamanho, no entanto, o Manual do BR Code diz que apenas os seguintes caracteres podem ser utilizados: • letras: de A a Z (somente maiúsculas); • dígitos de 0 a 9; • os seguintes caracteres especiais: $ % * + - . / : • o caractere de espaço em branco.

Realizamos alguns testes e apenas os PSPs Itaú e Santander não conseguem realizar decode de QR CODE com alguns dos caracteres especiais especificados acima, impossibilitando assim o pagamento, enquanto outras instituições conseguem realizar decode com esses e outros caracteres especiais, como acento agudo, por exemplo.

Em uma situação como essa qual deveria ser o melhor caminho a seguir?

Obs: Uma alternativa seria padronizar o Manual de iniciação e o Manual do BR Code adicional ao Manual de iniciação a limitação de caracteres especiais.
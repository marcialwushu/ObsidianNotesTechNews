---
link: https://github.com/bacen/pix-dict-api/issues/24
author: jgslima
published: 2021-05-06T14:54:00
tags: []
---
# Highlights


---
# Permitir mais robustez no cadastro de claims
Quando um PSP tenta cadastrar uma claim chamando o serviço "Criar Reivindicação", o PSP está sujeito a passar por um cenário onde o PSP sofre um crash após obter a response do serviço (ou após iniciar a request para o serviço) e antes de salvar no seu ambiente os dados da claim criada. Já passamos por este problema algumas poucas vezes o que causou transtorno.

Hoje, não há forma efetiva do PSP lidar com esta questão. O PSP pode, antes de fazer a requisição, salvar em seu ambiente a intenção de criar a claim, de forma que se o crash ocorrer, ele pode ter um processo de recuperação ou de retry. Só que, se o PSP tenta cadastrar a claim novamente, ele recebe o erro `ClaimAlreadyExistsForKey`. Ao ocorrer isso, o PSP até pode _assumir_ que esta claim que já existe é a claim que ele está tentando criar. Mas isto não é muito seguro. O mais correto seria, ao receber este erro, o PSP ter como consultar os dados desta claim no lado do DICT, para confirmar que trata-se mesmo da claim que ele queria registrar. Só que o PSP neste ponto, não tem em mãos o ID da claim para consultar por ele (visto que na primeira tentativa houve o crash). E utilizar o serviço "Listar Reivindicações" para tentar encontrar a claim não é efetivo.

O melhor seria que a API tivesse uma destas duas alterações/melhorias:

-   ao retornar `ClaimAlreadyExistsForKey`, retornar também o ID da claim.

ou

-   o serviço "Listar Reivindicações" passar a ter uma opção de filtro sobre o valor da chave.

A primeira alteração seria mais direta e mais voltada para este problema em específico. A segunda alteração (incluir filtro da chave no serviço "Listar Reinvindicações") poderia ajudar a resolver outros tipos de situações também.
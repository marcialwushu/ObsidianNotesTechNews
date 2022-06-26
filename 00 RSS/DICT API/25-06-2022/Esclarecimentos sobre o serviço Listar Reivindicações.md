---
link: https://github.com/bacen/pix-dict-api/issues/21
author: jgslima
published: 2021-04-20T18:03:00
tags: []
---
# Highlights


---
# Esclarecimentos sobre o serviço "Listar Reivindicações"
Notamos que na versão 1.2.0 da API foi incluída a observação sobre este serviço:

"_A atualização de informações de reinvindicações para listagens é assíncrona em relação às operações de inclusão e atualização de registros, sendo assim, é possível haver um retardo de 5 segundos até que os dados incluídos ou alterados constem na consulta._"

Estamos deixando de puxar algumas respostas do Doador o que está causando transtornos. Por isto é importante para nós termos os seguintes esclarecimentos.

**1) Tempo do delay** É esperado que o delay para que alterações nas reinvindicações sejam refletidas na consulta possa ser na prática maior do que 5 segundos?

**2) Valor efetivo do campo `LastModified` após uma alteração ser refletida na consulta** Quando o Doador atua sobre a claim alterando seu status, e quando ocorre um delay até a alteração do status ser refletida no serviço "_Listar Reivindicações_", o valor do campo `LastModified` da claim será o timestamp de quando a alteração de status ocorreu originalmente, ou será o timestamp de quando ela passou a constar na consulta?

Exemplo:

1.  `01:44:00` => Doador cancela a claim
2.  delay
3.  `01:44:05` => alteração passa a ser refletida na consulta.

A partir deste momento, a claim será considerada na consulta com `LastModified` igual a `01:44:00` ou igual a `01:44:05`?

**3) Alterações em claims serem refletidas fora de ordem** Se a resposta da pergunta anterior for que o `LastModified` será sempre a data/hora original da atualização de status, devido ao aspecto assíncrono da atualização de informações, pode ocorrer da atualização da listagem ser feita fora de ordem?

Por exemplo, o seguinte cenário poderia ocorrer?

1.  `01:44:00` => Doador cancela a Claim 1.
2.  `01:44:02` => Doador cancela a Claim 2.
3.  delay
4.  `01:44:03` => alteração da Claim **2** passa a ser refletida na consulta, com valor de `LastModified` igual a `01:44:02`.
5.  `01:44:05` => alteração da Claim **1** passa a ser refletida na consulta, com valor de `LastModified` igual a `01:44:00`.

Obrigado
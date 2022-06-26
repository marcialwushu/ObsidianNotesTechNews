---
link: https://github.com/bacen/pix-dict-api/issues/11
author: luizlaydner
published: 2020-10-16T12:32:00
tags: []
---
# Highlights


---
# [PROPOSTA] Adição de parâmetro role para filtragem na operação de listClaims
**Motivação**: Os filtros _isDonor_, _isClaimer_ da operação de [listClaims](https://www.bcb.gov.br/content/estabilidadefinanceira/pix/API_do_DICT-v1.0.html#operation/listClaims) não tem comportamento muito claro para algumas combinações de valores. Além disso, a especificação não deixa bem definido se esses filtros se combinam como conjunção (AND) ou como disjunção (OR). Por fim, há ainda que se considerar o comportamento quando o valor de um desses parâmetros não é passado. Essa complexidade toda deixa a API menos intuitiva e mais propensa a erros de implementação.

**Proposta**: Adicionar um parâmetro **role**, que poderia assumir os valores DONOR ou CLAIMER, na filtragem de listClaims. Para manter a compatibilidade da API, os parâmetros _isDonor_ e _isClaimer_ continuariam a existir e teriam sua definição com base em uma equivalência ao parâmetro role. Algumas combinações "estranhas" (não utilizadas na prática) passariam a ser inválidas.

A tabela abaixo resume o comportamento atual da API e o comportamento com a nova definição.

isDonor

IsClaimer

Comportamento atual

Nova definição em termos de "role"

True

True

Retorna claims em que participante é doador OU reivindicador

Inválido

True

Retorna claims em que participante é doador

role=DONOR

True

False

Retorna claims em que participante é doador

role=DONOR

False

True

Retorna claims em que participante é reivindicador

role=CLAIMER

False

Retorna claims em que participante é reivindicador

role=CLAIMER

False

False

Retorna claims em que participante é doador OU reivindicador

Inválido!

True

Retorna claims em que participante é reivindicador

role=CLAIMER

False

Retorna claims em que participante é reivindicador [(bug!)](https://github.com/bacen/pix-perguntas-e-respostas/issues/306)

role=DONOR

Retorna claims em que participante é doador OU reivindicador

role=

**Perguntas**:

-   Essa evolução da API a deixaria mais intuitiva ?
-   Uma futura remoção dos parâmetros isDonor e isClaimer, com a substituição pelo parâmetro role, teria impacto muito grande de implementação no seu participante?

**Proposta complementar**: Tornar o parâmetro **role** obrigatório.

A fim de simplificar o desenho do backend do DICT, melhorar o desempenho da query e diminuir o consumo de recursos no SGBD, estamos considerando a alternativa de tornar o parâmetro role obrigatório.

**Perguntas**:

Tornar esse parâmetro obrigatório teria impacto de implementação muito grande no seu participante ?
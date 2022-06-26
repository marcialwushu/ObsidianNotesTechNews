---
link: https://github.com/bacen/pix-dict-api/issues/47
author: GabrielSouzasbl
published: 2022-01-25T15:08:00
tags: []
---
# Highlights


---
# [PROPOSTA] Adição de parâmetro "ReportedBy" para filtragem na operação de listInfractions
Atualmente, é possível filtrar as infrações em que o PSP é o debitado e/ou creditado, independente se ele foi o criador ou não da infração, e isso, em alguns casos,, retorna muitos registros desnecessários. Há momentos em que é importante saber, por exemplo, apenas as infrações que foram criadas pelo PSP debitado.

A sugestão do filtro "reportedBy" poderia otimizar a pesquisa, já que o PSP criador da infração pode ser, ora o debitado ora o creditado.
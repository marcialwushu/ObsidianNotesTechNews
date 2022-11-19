# Nível de impacto 5 (IL5) do Departamento de Defesa (DoD)


## [](https://learn.microsoft.com/pt-br/compliance/regulatory/offering-dod-il5#dod-il5-overview)Visão geral do DoD IL5

A DISA (Agência de Sistemas de Informações de Defesa) é uma agência do Departamento de Defesa dos EUA (DoD) responsável por desenvolver e manter o [SRG (](https://dl.dod.cyber.mil/wp-content/uploads/cloud/SRG/index.html)Guia de Requisitos de Segurança de Computação em Nuvem) do DoD. O SRG define os requisitos de segurança de linha de base usados pelo DoD para avaliar a postura de segurança de um provedor de serviços de nuvem (CSP), dando suporte à decisão de conceder uma Pa (Autorização Provisória) do DoD que permita que um CSP hospede missões do DoD. Ele incorpora, substitui e cancela o CSM (Modelo de Segurança de Nuvem) do DoD publicado anteriormente e é mapeado para o RMF (DoD Risk Management Framework).

A DISA orienta as agências e departamentos do DoD no planejamento e autorização do uso de um CSP. Ele também avalia as ofertas de CSP para conformidade com o SRG, um processo de autorização no qual os CSPs podem fornecer documentação que defina sua conformidade com os padrões do DoD. Ele emite PAs (Autorizações Provisórias) do DoD quando apropriado, para que as agências de DoD e as organizações de suporte possam usar serviços de nuvem sem precisar passar por um processo de aprovação completo por conta própria, economizando tempo e esforço.

De acordo com os Níveis de Impacto das Informações da Seção [3.2 do SRG](https://dl.dod.cyber.mil/wp-content/uploads/cloud/SRG/index.html#3.2InformationImpactLevels)_, as_ informações do IL5 abrangem:

-   CUI (informações não classificadas controladas) que exigem um nível mais alto de proteção do que o fornecido pelo IL4
    
    -   O [Registro CUI](https://www.archives.gov/cui) fornece categorias específicas de informações que estão sob proteção do Branch Executivo, por exemplo, mais de 20 agrupamentos de categorias estão incluídos na lista de categorias [cui](https://www.archives.gov/cui/registry/category-list).
    -   [NIST SP 800-171](https://csrc.nist.gov/publications/detail/sp/800-171/rev-2/final) Proteger informações controladas não classificadas em sistemas e organizações _nãofederais_ destina-se a uso por agências federais em contratos ou outros contratos estabelecidos com organizações não federais.
-   NSS (National Security Systems)
    
    -   [A Diretriz NIST SP 800-59](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-59.pdf) para identificar um sistema de informações como um _sistema_ de segurança nacional fornece definições de NSS.
    -   [CNSSI 1253](https://www.dcsa.mil/portals/91/documents/ctp/nao/CNSSI_No1253.pdf)_Security Categorization and Control Selection for National Security Systems_ provides guidance on the security standards that federal agencies should apply to categorize national security information.

O [memorando de 15 de dezembro de 2014 do DoD CIO](https://www.esi.mil/contentview.aspx?id=585) sobre diretrizes atualizadas sobre a aquisição e o uso dos Serviços de Computação em Nuvem Comercial declara que 'FedRAMP servirá como a linha de base de segurança mínima para todos os serviços de nuvem do DoD'. O SRG usa a linha de base FedRAMP Moderate em todos os níveis de impacto de informações (IL) e considera a Linha de Base Alta em alguns.

O uso do DoD da Seção [5.1.1 do SRG](https://dl.dod.cyber.mil/wp-content/uploads/cloud/SRG/index.html#5SECURITYREQUIREMENTS) dos Controles de Segurança _fedRAMP declara que um FedRAMP_ High PA, complementado com controles FedRAMP+ do DoD e aprimoramentos de controle (C/CEs) e requisitos no SRG, são usados para avaliar os CSPs para a concessão de um DOD PA na IL5. Independentemente de qual linha de base C/CE é usada como base para um FedRAMP High PA, considerações e/ou requisitos adicionais precisarão ser avaliados e aprovados antes que um PA do DoD possa ser concedido na IL5. Especificamente, a Seção [5.1.2](https://dl.dod.cyber.mil/wp-content/uploads/cloud/SRG/index.html#5SECURITYREQUIREMENTS) do _DoD FedRAMP+ estados de controles/aprimoramentos_ de segurança do DoD na Tabela 2 que 10 C/CEs adicionais além da linha de base FedRAMP High são necessárias para um Pa do DoD IL5.

Além disso, de acordo com a Seção [SRG 5.2.2.3](https://dl.dod.cyber.mil/wp-content/uploads/cloud/SRG/index.html#5.2LegalConsiderations) Requisitos de Localização e Separação _il5_, os seguintes requisitos (entre outros) devem estar em vigor para um NÍVEL 5 PA:

-   A separação virtual/lógica entre locatários/missões do DoD e do Governo Federal é suficiente. A separação virtual/lógica entre sistemas de locatário/missão é necessária.
-   A separação física de locatários não do Governo Federal/não DoD (ou seja, locatários públicos, locais/governamentais) é necessária.
-   O CSP restringe o possível acesso às informações do DoD e da comunidade aos funcionários do CSP que são cidadãos americanos.
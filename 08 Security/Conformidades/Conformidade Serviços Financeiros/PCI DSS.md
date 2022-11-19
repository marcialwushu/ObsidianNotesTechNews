# Padrão de Segurança de Dados (DSS) da Indústria de Cartões de Pagamento (PCI)



## [](https://learn.microsoft.com/pt-br/compliance/regulatory/offering-pci-dss#pci-dss-overview)Visão geral do PCI DSS

O DSS (Padrão de Segurança de Dados) da PCI (Indústria de Cartões de Pagamento) é um padrão de segurança de informação global criado para prevenir fraudes por meio do maior controle de dados de cartões de crédito. Organizações de todos os tamanhos devem seguir os padrões PCI DSS se aceitarem cartões de pagamento das cinco principais marcas de cartão de crédito: Visa, MasterCard, American Express, Discover e Japan Credit Bureau (JCB). A conformidade com o PCI DSS é obrigatória para toda empresa que armazene, processe ou transmita dados de pagamento e do titular do cartão.


### Auditoria, relatórios e certificados do Office 365

-   [Atestado de Conformidade ( AoC) PCI DSS do OneDrive for Business e SharePoint Online](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuideV3?command=Download&downloadType=Document&downloadId=f1962237-32ea-4123-939e-1c8f04d13c16&tab=7027ead0-3d6b-11e9-b9e1-290b1eb4cdeb&docTab=7027ead0-3d6b-11e9-b9e1-290b1eb4cdeb_PCI_DSS)

### [](https://learn.microsoft.com/pt-br/compliance/regulatory/offering-pci-dss#frequently-asked-questions)Perguntas frequentes

**Por que a página de rosto do Atestado de Conformidade (AoC) mostra “Junho de 2018”?**

A data de junho de 2018 na página de rosto é de quando o modelo de AoC foi publicado. Consulte a data da avaliação na Seção 2.

**Qual é a relação entre PA DSS e PCI DSS?**

O Padrão de Segurança de Dados em Aplicativos de Pagamento (Payment Application Data Security Standard - PA DSS) é um conjunto de requisitos que cumpre o PCI DSS e substitui as Práticas Recomendadas para Aplicativos de Pagamento da Visa (Visa’s Payment Application Best Practices) e consolida os requisitos de conformidade dos outros emissores de cartões principais. O PA DSS ajuda os fornecedores de software a desenvolver aplicativos de terceiros para armazenar, processar ou transmitir dados de pagamento do titular do cartão como parte do processo de autorização ou pagamento do cartão. Os varejistas precisam usar aplicativos com a certificação PA DSS para obter efetivamente a conformidade com o PCI DSS. O PA DSS não se aplica ao Azure.

**O que é um adquirente? O Azure usa um?**

Os adquirentes são bancos ou outras entidades que processam transações de cartões de pagamento. O Azure não oferece o serviço de processamento de cartões de pagamento e, portanto, não utiliza um adquirente.

**A quais organizações e comerciantes o PCI DSS se aplica?**

O PCI DSS se aplica a qualquer empresa, independentemente do tamanho ou do número de transações que aceite, transmita ou armazene dados de titulares de cartões. Ou seja, se qualquer cliente pagar uma empresa usando um cartão de crédito ou débito, os requisitos do PCI DSS se aplicarão. As empresas são validadas em um dos quatro níveis de acordo com o volume total de transações durante um período de 12 meses. O Level 1 engloba empresas que processam mais de 6 milhões de transações por ano; o Level 2, de 1 milhão a 6 milhões de transações; o Level 3, de 20.000 a 1 milhão de transações e o Level 4, para menos de 20.000 transações.

**Há planos para que o OneDrive for Business e o SharePoint Online estejam em conformidade com o PCI DSS fora dos Estados Unidos?**

Atualmente, o OneDrive for Business e o SharePoint Online estão em conformidade com o PCI DSS somente nos Estados Unidos (EUA). A Microsoft avaliará os requisitos e as linhas do tempo em outras regiões fora dos EUA e fornecerá atualizações quando e se outras regiões forem adicionadas ao roteiro.

**O que está no escopo do OneDrive for Business e do Microsoft Office SharePoint Online?**

Atualmente, apenas os arquivos e documentos carregados no OneDrive for Business e no SharePoint Online estarão em conformidade com o PCI DSS.

### [](https://learn.microsoft.com/pt-br/compliance/regulatory/offering-pci-dss#use-microsoft-compliance-manager-to-assess-your-risk)Use o Gerenciador de Conformidade da Microsoft para avaliar o risco

O[Gerenciador de Conformidade da Microsoft](https://learn.microsoft.com/pt-br/microsoft-365/compliance/compliance-manager) é um recurso no [Centro de conformidade do Microsoft 365](https://learn.microsoft.com/pt-br/microsoft-365/compliance/microsoft-365-compliance-center) para ajudá-lo a entender a postura de conformidade da sua organização e executar ações para ajudar a reduzir os riscos. O Gerenciador de Conformidade oferece um modelo premium para criar uma avaliação para essa regulamentação. Encontre o modelo na página **modelos de avaliação** no Gerenciador de Conformidade. Saiba como [criar avaliações no Compliance Manager](https://learn.microsoft.com/pt-br/microsoft-365/compliance/compliance-manager-assessments).

### [](https://learn.microsoft.com/pt-br/compliance/regulatory/offering-pci-dss#resources)Recursos

-   [Conselho de Padrões de Segurança (Security Standards Council) do PCI](https://www.pcisecuritystandards.org/)
-   [Padrão de Segurança de Dados (Data Security Standard) do PCI](https://www.pcisecuritystandards.org/documents/PCI_DSS_v3-1.pdf)
-   [Guia de Referência (Quick Reference Guide) do PCI DSS](https://www.pcisecuritystandards.org/documents/PCISSC%20QRG%20August%202014%20-print.pdf)
-   [Conformidade na Central de Confiabilidade da Microsoft](https://www.microsoft.com/trust-center/compliance/compliance-overview)

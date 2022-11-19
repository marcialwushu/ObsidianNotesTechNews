## Visão geral do PCI 3DS

Europay, Mastercard e Visa (EMV) seguro de três domínios ([3-D Secure](https://www.emvco.com/emv-technologies/3d-secure/)ou 3DS) é um protocolo de mensagens EMVCo que permite que os titulares de cartões se autentiquem com seus emissores de cartões ao fazer transações on-line de cartão não presente (CNP). A especificação visa proteger a autenticação e a verificação de identidade em aplicativos móveis e baseados em navegador. A camada de segurança adicional ajuda a impedir transações CNP não autorizadas e protege o comerciante da exposição a fraudes CNP.

Os três domínios na especificação EMVCo incluem:

-   Domínio do adquirente: as transações do 3DS são iniciadas a partir do domínio **do adquirente**. Os componentes sob esse domínio são o 3DS Server (3DSS), o ambiente solicitante, o integrador e o adquirente.
-   **Domínio de interoperabilidade:** Facilita a transferência de informações de transação entre o domínio do adquirente e o domínio do emissor. Os componentes sob esse domínio são o 3DS Directory Server (DS), a Directory Server Certificate Authority (DS-CA) e o sistema de autorização.
-   Domínio do emissor:as transações do 3DS são autenticadas no domínio **do emissor**. Os componentes sob esse domínio são o 3DS Access Control Server (ACS), o titular do cartão, o dispositivo de consumo e o emissor.

Os três componentes ou funções críticas do EMV 3DS nesses domínios incluem:

-   Servidor 3DS (3DSS)
-   Servidor de diretório 3DS (DS)
-   Servidor de Controle de Acesso (ACS) 3DS

O PCI 3DS[Core Security Standard](https://www.pcisecuritystandards.org/document_library)fornece uma estrutura para essas funções críticas do EMV 3DS para implementar controles de segurança que suportam a integridade e a confidencialidade das transações do 3DS. O padrão se aplica a entidades que executam ou fornecem essas funções (3DSS, DS e ACS), conforme definido na[Especificação Principal do EMVCo 3DS](https://www.emvco.com/emv-technologies/3d-secure/). Provedores de serviços terceirizados que podem afetar essas funções do 3DS ou a segurança dos ambientes onde essas funções são executadas também podem ser necessários para atender aos requisitos do PCI 3DS. Se uma entidade é obrigada a validar a conformidade com o PCI 3DS Core Security Standard é definido pelos programas de conformidade de marca de pagamento individual.

## Relatórios de auditoria

Você pode acessar os documentos de auditoria do Azure PCI 3DS na seção Relatórios do Portal de Confiança de Serviço (STP)[PCI DSS](https://servicetrust.microsoft.com/viewpage/PCI). Você deve entrar para acessar os relatórios de auditoria no STP. Para obter mais informações, consulte[Introdução ao Microsoft Service Trust Portal](https://aka.ms/stphelp). Os seguintes documentos estão incluídos no pacote PCI 3DS do Azure (arquivo compactado):

-   Atestado de Conformidade (AoC)
-   Matriz de Responsabilidade Compartilhada
-   Whitepaper (em inglês)

## [](https://learn.microsoft.com/pt-br/azure/compliance/offerings/offering-pci-3ds?toc=%2Fcompliance%2Fregulatory%2Ftoc.json&bc=%2Fcompliance%2Fregulatory%2Fbreadcrumb%2Ftoc.json#frequently-asked-questions)Perguntas frequentes

**Por que a capa do Atestado de Conformidade (AoC) diz "dezembro de 2017"?**  
A data de dezembro de 2017 na folha de rosto é quando o modelo AoC foi publicado. Consulte a Secção 3 com assinaturas para a data da avaliação.

**Por quanto tempo o PCI 3DS AoC é válido?**  
O período efetivo para conformidade começa após a aprovação na auditoria e o recebimento da AoC do avaliador da 3DS e termina um ano a partir da data em que a AoC é assinada.

**Onde posso obter a documentação de auditoria do Azure PCI 3DS?**  
Para obter links para a documentação de auditoria, consulte[Relatórios de auditoria](https://learn.microsoft.com/pt-br/azure/compliance/offerings/offering-pci-3ds?toc=%2Fcompliance%2Fregulatory%2Ftoc.json&bc=%2Fcompliance%2Fregulatory%2Fbreadcrumb%2Ftoc.json#audit-reports). Você deve ter uma assinatura existente do Azure ou[uma conta de avaliação gratuita do Azure](https://azure.microsoft.com/free/)para entrar. Em seguida, você pode baixar certificados de auditoria, relatórios de avaliação e outros documentos aplicáveis para ajudá-lo com seus próprios requisitos normativos.

**Quais regiões e serviços do Azure estão no escopo da avaliação?**  
Consulte "Locais" e "Descrição do Ambiente" na Seção 2 para obter uma lista de regiões e serviços do Azure no escopo da avaliação do PCI 3DS.

**Quem tem de cumprir a Norma de Segurança PCI 3DS Core?**  
O padrão destina-se a empresas que gerenciam ou fornecem funções 3DS, especificamente: 3DSS, DS e ACS. Ele fornece diretrizes para identificar e implementar controles de segurança apropriados para proteger o processo de transação do 3DS.

**Qual é a relação entre o PCI 3DS Core Security Standard e o PCI DSS?**  
O PCI 3DS Core Security Standard e o PCI DSS são padrões separados, cada um destinado a tipos específicos de entidades. O PCI 3DS Core Security Standard aplica-se a ambientes 3DS onde as funções 3DSS, DS e ACS são executadas, enquanto o PCI DSS se aplica onde quer que os dados da conta do cartão de pagamento sejam armazenados, processados ou transmitidos.

**Como uma entidade 3DS deve gerenciar um ambiente coberto pelo PCI 3DS e pelo PCI DSS?**  
Se você for uma entidade 3DS que armazena, processa ou transmite dados de conta de cartão de pagamento, você terá um ambiente 3DS definido (3DE) e um ambiente de dados de titular de cartão (CDE) definido. Se os dados da conta estiverem presentes no ambiente onde as funções do 3DS são executadas, esse ambiente será considerado um 3DE e um CDE. Quando o 3DE e o CDE são combinados no mesmo ambiente, você poderá implementar controles de segurança que atendam aos requisitos de ambos os padrões.

Se você é obrigado a validar a conformidade com o PCI 3DS Core Security Standard e/ou PCI DSS é definido pelos programas de conformidade de marca de pagamento individual. Para obter mais informações, consulte o documento[de perguntas frequentes do PCI 3DS Core Security Standard](https://www.pcisecuritystandards.org/documents/FAQs_for_PCI_3DS_Core_Security_Standard.pdf).

**Por onde começo os esforços de conformidade com o PCI 3DS da minha organização para uma solução implantada no Azure?**  
As informações que o PCI Security Standards Council (PCI SSC) disponibiliza são um bom lugar para aprender sobre requisitos específicos de conformidade. O PCI[SC publica](https://www.pcisecuritystandards.org/document_library)o PCI 3DS Core Security Standard e documentos de suporte que explicam como você pode ajudar a proteger seu processo de transação 3DS. Além do Atestado de Conformidade (AoC) do PCI 3DS do Azure, a Microsoft fornece documentos de orientação, como a Matriz de Responsabilidade Compartilhada do Azure PCI 3DS e o whitepaper do Azure PCI 3DS para ajudá-lo a atender aos seus próprios requisitos de conformidade.

## [](https://learn.microsoft.com/pt-br/azure/compliance/offerings/offering-pci-3ds?toc=%2Fcompliance%2Fregulatory%2Ftoc.json&bc=%2Fcompliance%2Fregulatory%2Fbreadcrumb%2Ftoc.json#resources)Recursos

-   [Documentação de conformidade do Azure](https://learn.microsoft.com/en-us/azure/compliance/)
-   [O Azure permite um mundo de conformidade](https://azure.microsoft.com/resources/azure-enables-a-world-of-compliance/)
-   [Ofertas de conformidade com o Microsoft 365](https://learn.microsoft.com/en-us/compliance/regulatory/offering-home)
-   [Conformidade na Central de Confiabilidade da Microsoft](https://www.microsoft.com/trust-center/compliance/compliance-overview)
-   [EMVCo 3DS Core Especificação](https://www.emvco.com/emv-technologies/3d-secure/)
-   [PCI Security Standards Council](https://www.pcisecuritystandards.org/) (PCI SSC)
-   [Padrão de segurança PCI 3DS Core](https://www.pcisecuritystandards.org/document_library)
-   [Microsoft Cloud para serviços financeiros](https://www.microsoft.com/industry/financial-services/microsoft-cloud-for-financial-services)
-   [Soluções do Azure para o setor financeiro](https://learn.microsoft.com/en-us/azure/architecture/industries/finance)
-   [Recursos de serviços financeiros da Microsoft](https://servicetrust.microsoft.com/ViewPage/FinancialServices2)no Portal de Confiança de Serviço
-   [Programa de conformidade de serviços financeiros do Microsoft Cloud](https://aka.ms/FSCP-Print)
-   [Mapa de conformidade dos princípios regulatórios da computação em nuvem e dos serviços online da Microsoft](https://servicetrust.microsoft.com/DocumentPage/5b483567-00b0-4d86-96ae-ee887dadb61c)
-   [Guia de avaliação de risco e conformidade para instituições financeiras no Microsoft Cloud](https://azure.microsoft.com/resources/risk-assessment-and-compliance-guide-for-financial-institutions-in-the-microsoft-cloud-/)
-   [Mapa de conformidade dos princípios regulatórios da computação em nuvem e dos serviços online da Microsoft](https://servicetrust.microsoft.com/DocumentPage/5b483567-00b0-4d86-96ae-ee887dadb61c)


---
link: https://insights.sei.cmu.edu/blog/system-resilience-what-exactly-is-it/
author: {{author}}
published: {{published}}
tags: [{{tags:,}}]
---
# Highlights
{{highlights}}

---
# Resiliência do Sistema: O que exatamente é?
Na última década, a [resiliência do sistema](https://www.incose.org/incose-member-resources/working-groups/analytic/resilient-systems) (também conhecida como resiliência do sistema) tem sido amplamente discutida como uma preocupação crítica, especialmente em termos de data centers e computação em nuvem. Também é de vital importância para [sistemas cibernéticos,](https://insights.sei.cmu.edu/sei_blog/cyber-physical-systems/) embora o termo seja menos comumente usado nesse domínio. Todos querem que seus sistemas sejam resistentes, mas o que isso realmente significa? E como a resiliência se relaciona com outros [atributos de qualidade](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=12433), como disponibilidade, confiabilidade, robustez, segurança, segurança e sobrevivência? A resiliência é um componente de alguns ou todos esses atributos de qualidade, um superconjunto deles, ou outra coisa? Se quisermos garantir que os sistemas sejam resilientes, devemos primeiro saber a resposta a essas perguntas e entender exatamente o que é resiliência do sistema.

Como parte do trabalho sobre o desenvolvimento de requisitos de resiliência para sistemas cibernéticos físicos, concluí recentemente um estudo de literatura sobre padrões existentes e outros documentos relacionados à resiliência. Minha revisão revelou que o termo _resiliência_ é tipicamente usado informalmente como se seu significado fosse óbvio. Nos casos em que foi definido, foi dado significados semelhantes, mas um tanto inconsistentes.

Outra questão que encontrei foi que o termo _resiliência_ é usado em dois sentidos muito diferentes. O escopo deste post no blog, o primeiro de uma série de duas partes, foca na _resiliência do sistema_ e **não** na _resiliência organizacional_, que tem um escopo muito maior. A resiliência organizacional está principalmente preocupada com a continuidade dos negócios e inclui a gestão de pessoas, informação, tecnologia e instalações. Para obter mais informações sobre resiliência organizacional (com ênfase em processo e cibersegurança), consulte o [_CERT Resilience Management Model (CERT-RMM)_](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=508084).

**O que torna um sistema resistente?**

Basicamente, um sistema é resiliente se continuar a realizar sua missão diante das adversidades (ou seja, se fornece capacidades necessárias, apesar de estresses excessivos que podem causar interrupções). Ser resiliente é importante porque não importa o quão bem um sistema seja projetado, a realidade mais cedo ou mais tarde conspirará para interromper o sistema. Defeitos residuais no software ou hardware eventualmente farão com que o sistema não execute corretamente uma função necessária ou faça com que ele não cumpra um ou mais de seus requisitos de qualidade (por exemplo, disponibilidade, capacidade, interoperabilidade, desempenho, confiabilidade, robustez, segurança, segurança e usabilidade). A falta ou falha de uma salvaguarda permitirá que um acidente ocorra. Uma vulnerabilidade de segurança desconhecida ou não corrigida permitirá que um invasor comprometa o sistema. Uma condição ambiental externa (por exemplo, perda de fornecimento elétrico ou temperatura excessiva) interromperá o serviço.

Devido a essas inevitáveis interrupções, a disponibilidade e a confiabilidade por si só são insuficientes e, portanto, um sistema também deve ser resiliente. Deve resistir às adversidades e prover a continuidade do serviço, possivelmente sob um modo de operação degradado, apesar dos distúrbios devido a eventos e condições adversas. Também deve se recuperar rapidamente de qualquer dano que essas perturbações possam ter causado. Como no antigo comercial da Timex, um sistema resiliente "pode levar uma lambida e continuar tique-taque".

No entanto, a resiliência do sistema é mais complexa do que a explicação anterior implica. A resiliência do sistema _não_ é uma simples função booleana (ou seja, um sistema não é meramente resistente ou não resistente). Nenhum sistema é 100% resistente a todos os eventos ou condições adversas. Resiliência é sempre uma questão de grau. A resiliência do sistema normalmente não é mensurável em uma _única_ escala ordinal. Em outras palavras, pode não fazer sentido dizer que o sistema A é mais resistente do que o sistema B.

Para entender completamente a resiliência, ela deve ser decomposta em suas partes componentes. Para exibir resiliência, um sistema deve incorporar controles que detectem eventos e condições adversas, responder adequadamente a esses distúrbios e se recuperar rapidamente depois. Como a resiliência pressupõe que ocorrerão eventos e condições adversas, os controles que impedem as adversidades estão fora do escopo da resiliência.

Alguns controles de resiliência suportam a detecção, enquanto outros controles suportam resposta ou recuperação. Um sistema pode, portanto, ser resiliente em alguns aspectos, mas não em outros. O sistema A pode ser o mais resistente em termos de detectar certos eventos adversos, enquanto o sistema B pode ser o mais resistente em termos de resposta a outros eventos adversos. Por outro lado, o sistema C pode ser o mais resistente em termos de recuperação de um tipo específico de dano causado por certos eventos adversos.

É importante entender o escopo do que significa para um sistema resistir às adversidades:

-   Quais capacidades/serviços críticos o sistema deve continuar fornecendo apesar das interrupções?
-   Que tipos de adversidades podem interromper a entrega dessas capacidades críticas (ou seja, quais eventos e condições adversas o sistema deve ser capaz de tolerar)?
-   Quais são os tipos e níveis de dano a quais ativos que podem causar essas interrupções?

Os pontos anteriores levam a uma definição mais detalhada e matizada de resiliência do sistema:

Um sistema é _resiliente_ ao grau em que protege rapidamente e efetivamente suas _capacidades críticas_ contra interrupções causadas por _eventos e condições adversas_.

Implícita na definição anterior é a ideia de que ocorrerão eventos e condições adversas. A resiliência do sistema é sobre o que o sistema faz quando esses eventos potencialmente disruptivos ocorrem e existem condições. O sistema detecta esses eventos e condições? O sistema responde corretamente a eles assim que são detectados? O sistema se recupera corretamente depois?

Some organizations \[[MITRE 2019](https://www.researchgate.net/publication/334549424_Systems_Engineering_for_Resilience)\] include the avoidance of adverse events and conditions within system resilience. However, this is misleading and inappropriate as avoidance falls outside of the definition of system resilience. Avoiding or preventing adversities does not make a system more resilient. Rather, avoidance decreases the need for resilience because systems would not need to be resilient if adversities never occurred.

A Figura 1 ilustra as relações entre os conceitos-chave na definição anterior de resiliência do sistema. Um sistema resiliente protege suas capacidades críticas (e ativos associados) contra danos usando técnicas de resiliência protetora para resistir passivamente a eventos e condições adversas ou detectar ativamente essas adversidades, responder a elas e se recuperar dos danos que causam. Como veremos no segundo post desta série, cada um desses eventos e condições adversas está associado a uma das seguintes características de qualidade subordinadas: robustez, segurança, cibersegurança (incluindo [anti-adulteração](http://acqnotes.com/acqnote/careerfields/anti-tamper)), [sobrevivência](https://en.wikipedia.org/wiki/Survivability#Military) militar, capacidade, longevidade e interoperabilidade.


![[Pasted image 20220709211903.png]]
_Figura 1: Conceitos-chave na definição de resiliência do sistema_

A Figura 2 mostra uma linha do tempo nocional de como um evento adverso pode ser gerenciado pela aplicação ordenada de controles de resiliência para retornar um sistema às operações normais.


![[Pasted image 20220709211951.png]]

_Figura 2: Exemplo de cronograma de resiliência_

Para entender o escopo completo e a complexidade da resiliência do sistema, é importante compreender os significados das palavras-chave itálicadas na definição anterior e como elas estão relacionadas na figura anterior.

_A proteção_ consiste nas seguintes quatro funções:

-   R_esistance_ é a capacidade do sistema de prevenir passivamente ou minimizar danos ocorridos durante o evento ou condição adversa. As técnicas de resiliência para resistência passiva incluem uma arquitetura modular que impede a propagação de falhas entre módulos, a falta de pontos únicos de falha e a blindagem de equipamentos elétricos, computadores e redes a partir de pulsos eletromagnéticos (EMP).
-   _Detecção_ é a capacidade do sistema de detectar ativamente (através de técnicas de detecção):

\- Perda ou degradação de capacidades críticas  
\- Danos aos ativos necessários para implementar capacidades críticas  
\- Eventos e condições adversas que podem causar danos a capacidades críticas ou ativos relacionados

-   _A reação_ é a capacidade do sistema de reagir ativamente à ocorrência de um evento adverso em curso ou responder à existência de uma condição adversa (pela qual a reação é implementada por técnicas de reação). Ao detectar uma adversidade, um sistema pode parar ou evitar o evento adverso, eliminar a condição adversa e, assim, eliminar ou minimizar danos adicionais. As técnicas de reação incluem a contratação de tratamento de exceção, modos de operação degradados e redundância com votação e
-   _A recuperação_ é a capacidade do sistema de se recuperar ativamente dos danos _após_ o fim do evento adverso (pelo qual a recuperação é implementada por técnicas de recuperação). A recuperação pode ser completa no sentido de que o sistema seja devolvido ao status operacional completo com todos os ativos danificados/destruídos que foram reparados ou substituídos. A recuperação também pode ser parcial (por exemplo, o serviço completo é restaurado usando recursos redundantes sem substituição/reparo) ou mínimo (por exemplo, operações de modo degradada que fornecem apenas serviços limitados). A recuperação também pode incluir a evolução ou adaptação do sistema (por exemplo, através da reconfiguração em si mesmo) para evitar futuras ocorrências dos eventos ou condições adversas.

_Os recursos do sistema_ são os serviços críticos que o sistema deve continuar a fornecer, apesar das interrupções causadas pelas adversidades.

_Os ativos_ são itens valiosos que devem ser protegidos contra danos causados por eventos e condições adversas porque implementam as capacidades críticas do sistema. Muitas vezes é impossível evitar completamente danos a todos os ativos sob todos os eventos e condições adversas. Os ativos são, portanto, tipicamente priorizados para que a detecção, a reação e a recuperação se concentrem em proteger os ativos mais importantes primeiro. Os ativos relevantes para a resiliência incluem os seguintes:

-   _Componentes do sistema_: subsistemas de componentes do sistema, hardware, software (por exemplo, aplicativos, infraestrutura, sistemas operacionais e firmware), redes (por exemplo, dispositivos, rádios e cabeamentos) e instalações
-   _Dados do sistema_: os dados que o sistema armazena, produz e manipula
-   _Sistema-Ativo externo_: quaisquer ativos do sistema externo (por exemplo, pessoas, propriedades, meio ambiente, fundos e reputação) pelos quais o sistema é responsável por proteger contra danos

_Os danos_ a esses ativos incluem o seguinte:

-   _Danos às Capacidades do Sistema_: a perda total ou parcial do serviço e roubo de serviço
-   _Danos aos Componentes do Sistema_: a destruição, dano a, roubo ou engenharia reversa não autorizada de hardware ou software
-   _Dano aos Dados_: perda de acesso (violações de disponibilidade), corrupção (violações de integridade), divulgação não autorizada (violações de sigilo e anonimato), repúdio a transações (violações de não repúdio) e engenharia reversa de informações críticas do programa (CPI) (violações anti-adulteração)
-   _Danos ao Sistema-Ativo Externo_: perda de fundos, perda de reputação, perda de negócios e danos ambientais ou destruição

_Eventos adversos_ são eventos que, devido ao seu estressante, podem interromper as capacidades críticas, causando danos aos ativos associados. Esses eventos adversos (com seus atributos de qualidade associados) incluem a ocorrência dos seguintes:

-   Eventos ambientais adversos, como a perda de energia elétrica externa do sistema, bem como desastres naturais como terremotos ou incêndios florestais (Robustez, especificamente tolerância ambiental)
-   Erros de entrada, como erro do operador ou do usuário (Robustez, especificamente tolerância a erros)
-   Falhas externamente visíveis para atender aos requisitos (Robustez, especificamente tolerância à falha)
-   Acidentes e quase falhas (Segurança)
-   Ataques de cibersegurança/adulteração (Cibersegurança e Anti-Tamper)
-   Ataques físicos de terroristas ou forças militares adversárias (Sobrevivência)
-   Picos de carga e falhas devido a cargas excessivas (Capacidade)
-   Falhas causadas pelo excesso de idade e desgaste (Longevidade)
-   Perda de comunicações (Interoperabilidade)

_Condições adversas_ são condições que, devido à sua natureza estressante, podem interromper ou levar à interrupção de capacidades críticas. Estas condições adversas incluem a existência do seguinte:

-   Condições ambientais adversas, como temperaturas excessivas e clima severo (Robustez, especificamente tolerância ambiental)
-   Falhas internas do sistema, como defeitos de hardware e software (Robustez, especificamente tolerância a falhas)
-   Riscos de segurança (Segurança)
-   Ameaças e vulnerabilidades de segurança cibernética (Cibersegurança e Anti-Tamper)
-   Ameaças e vulnerabilidades militares (Sobrevivência)
-   Cargas excessivas (Capacidade)
-   Idade e desgaste excessivos (Longevidade)
-   Comunicações degradadas (Interoperabilidade)

Observe que o anti-adulteração (AT) é um caso especial que, à primeira vista, pode parecer não estar relacionado à resiliência. O objetivo da AT é evitar que um adversário contraa informação de programa crítico de engenharia reversa (CPI) como software classificado. Especialistas anti-adulteração normalmente assumem que um adversário obterá a posse física do sistema contendo a CPI a ser engenharia reversa nesse caso, garantindo que o sistema continue funcionando apesar da adulteração seria irrelevante. No entanto, a adulteração também pode ser tentada remotamente (ou seja, sem antes adquirir a posse do sistema). Em situações em que o adversário não tem acesso, uma contramedida da AT pode ser detectar a tentativa remota de acesso e cópia da CPI de um adversário e, em seguida, responder [por zerar](https://en.wikipedia.org/wiki/Zeroisation) a CPI, momento em que o sistema não estaria mais operacional. Assim, a adulteração remota tem ramificações de resiliência.

**Embrulhando e olhando para frente**

Este primeiro post sobre resiliência do sistema fornece uma definição detalhada e matizada do atributo de qualidade de resiliência do sistema. No [segundo post desta série](https://insights.sei.cmu.edu/blog/system-resilience-part-2-how-system-resilience-relates-to-other-quality-attributes/), explicarei como essa definição esclarece como a resiliência do sistema se relaciona com outros atributos de qualidade intimamente relacionados.

**Recursos adicionais**

Leia o segundo post desta série sobre resiliência do sistema, [_como a resiliência do sistema se relaciona com outros atributos de qualidade_](https://insights.sei.cmu.edu/blog/system-resilience-part-2-how-system-resilience-relates-to-other-quality-attributes/).

Leia o terceiro post desta série sobre resiliência do sistema, [_Requisitos do Sistema de Engenharia_](https://insights.sei.cmu.edu/blog/system-resilience-part-3-engineering-system-resilience-requirements/)_._

\[Caralli et al. 2016\] Richard A. Caralli, Julia H. Allen, David W. White, Lisa R. Young, Nader Mehravari, Pamela D. Curtis, [_CERTÂ® Resilience Management Model, Versão 1.2, Resilient Technical Solution Engineering_](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=508084), SEI, Fevereiro 2016.

\[Firesmith 2003\] Donald G. Firesmith, [_Common Concepts Underlying Safety, Security, and Survivability Engineering_,](http://donaldfiresmith.me/wp-content/uploads/2018/12/2003-170-Common-Concepts-Underlying-SEI.pdf) Technical Note CMU/SEI-2003-TN-033, Software Engineering Institute, Pittsburgh, Pensilvânia, dezembro de 2003, 75 páginas.

\[[ISO/IEC 25010:2011](https://www.iso.org/standard/35733.html)\] Sistemas e Engenharia de Software -- Requisitos e Avaliação de Qualidade de Sistemas e Software (SQuaRE) -- Modelos de Qualidade de Sistemas e Software

\[[ISO/IEC 15026-1:2013](https://www.iso.org/standard/62526.html)\] _Sistemas e engenharia de software - Sistemas e garantia de software - Parte 1: Conceitos e vocabulário_

\[[ISO/IEC/IEEE 24765:2017](https://www.iso.org/standard/71952.html)\] Engenharia de sistemas e software - Vocabulário

\[[MITRE 2019](https://www.researchgate.net/publication/334549424_Systems_Engineering_for_Resilience)\] John S. Brtis, Michael A. McEvilley, _Engenharia de Sistemas para Resiliência_, MITRE, julho de 2019
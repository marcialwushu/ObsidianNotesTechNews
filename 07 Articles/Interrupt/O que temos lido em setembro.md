
Aqui estão os artigos, vídeos e ferramentas que estamos animados com isso Setembro

Esperamos que você goste desses links, e estamos ansiosos para ouvir o que você tem sido leitura nos comentários ou[no Interrupt Slack](https://interrupt-slack.herokuapp.com/).

## Artigos & Aprendizado[](https://interrupt.memfault.com/blog/september-2022-roundup#articles--learning)

-   [**Como construir e manter sistemas de gerenciamento de IoT para escala (Memfault Webinar)**](https://www.youtube.com/watch?v=6X62qDaNaNc) por Tyler Hoffman & Chris Coleman  
    Eu tive uma explosão fazendo um webinar conjunto com Chris falando sobre como construir equipes de engenharia e sistemas de dados para garantir que equipes de firmware e empresas de hardware possam construir produtos e infraestrutura confiáveis. Parece um bocado, mas honestamente, o webinar era Chris contando a todos histórias divertidas do passado, o que é sempre um bom momento.
    
-   [**Como De-Risk Product Launches with Device Reliability Engineering (Memfault Webinar)**](https://www.youtube.com/watch?v=OFq3aupQp64) por François Baldassari  
    Sinto que aprendo muito com cada webinar que François dá. Neste, ele fala sobre TDD, atualizações do Dia-0, por que e como construir uma Camada de Abstração de Hardware (HAL), e por que você deve dividir a construção de firmware de fabricação e o firmware operacional normal. Estes são todos estes que ele aprendeu ao longo de seu tempo em Pebble, Oculus, e Memfault.
    
-   [**Open Source Firmware Conference 2022 (Vídeos)**](https://www.osfc.io/2022/schedule/)  
    Os vídeos da Open Source Firmware Conference 2022 foram postados online. Confira!
    
-   [**Depurando C no CANPicod - Dr. Ken Tindell**](https://kentindell.github.io/2022/07/26/canpico-c-debug/)  
    Um artigo rápido detalhando como se levantar e executar depurando o CANPico, que é baseado no Raspberry Pi Pico (RP2040). -Tyler
    
-   [**O Livro do Sistema CP de**](https://fabiensanglard.net/cpsb/index.html)Fabien Sanglard  
    Um livro sobre o hardware e software dentro das máquinas de moedas de ontem, como Street Fighter. -Tyler
    
-   [**Anel totalmente oxidante: Criando uma pilha de TLS de Ferrugem Pura Com base em`rustls`+`ring`" o coelhinho do blog do coelhinho**](https://www.bunniestudios.com/blog/?p=6521)  
    está tentando construir um sistema operacional inteiramente baseado em ferrugem, [Xous OS](https://betrusted.io/xous-book/ch00-00-introduction.html), e este artigo é sobre a construção de uma pilha de TLS com Rust.
    
-   [**Embedded Systems And The Volatile Keyword - mbedded.ninja**](https://blog.mbedded.ninja/programming/languages/c/embedded-systems-and-the-volatile-keyword/)por Geoffrey Hunter  
    Um artigo detalhando quando e por que um engenheiro incorporado usaria a palavra-chave.`volatile`
    
-   [**Nomes de componentes de software devem ser caprichosos e enigmáticos - Melhor programação**](https://betterprogramming.pub/software-component-names-should-be-whimsical-and-cryptic-ca260b013de0)  
    A peça afirma que os componentes de software que são caros para renomear (por exemplo, nomes de pacotes para um gerenciador de pacotes públicos) devem tentar não evitar nomes que expliquem o que fazem. Em vez disso, deve-se tratar seu nome como apenas uma "alça", mas otimizado para os humanos: curto, memorável, alegre. - Heiko
    
-   [**Como o MQTT em Narrowband-IoT pode arruinar seu projeto - Design de Computação Embarcada**](https://embeddedcomputing.com/technology/iot/wireless-sensor-networks/how-mqtt-on-narrowband-iot-can-ruin-your-project)por Fabian Kochem  
    O que acontece quando você usa MQTT padrão com NB-IoT. Pode funcionar bem nos testes, mas falhar gloriosamente no campo. Se você usar um protocolo baseado em TCP em uma conexão UDP, você vai ter um momento ruim. Existe uma[versão UDP de MQTT](https://mqtt-udp.readthedocs.io/en/latest/), mas achamos que as pessoas devem usar o CoAP hoje em dia.
    
-   [**Alguém está mexendo com meus subnormais!**](https://moyix.blogspot.com/2022/09/someones-been-messing-with-my-subnormals.html)  
    Artigo incrível no qual o autor desce muito pelo buraco do coelho investigando o uso de todos :open\_mouth: pacotes python no PyPi. -Noé`-ffast-math`
    
-   [**O tutorial GNU Debugger do desenvolvedor GDB, Parte 1: Começando com o depurador - Red Hat Developer**](https://developers.redhat.com/blog/2021/04/30/the-gdb-developers-gnu-debugger-tutorial-part-1-getting-started-with-the-debugger)de Keith Seitz  
    Série Eu gostaria de ter lido mais cedo! -Noé
    
-   [**Dumping do firmware Tuya**](https://jilles.com/posts/tuya/)por Jilles Groenendijk  
    A aventura comprando hardware barato e despejando o firmware baseado em Tuya.
    

-   [**wapiflapi/gxf: Gdb Extension Framework é um monte de código python em torno do api gdb.**](https://github.com/wapiflapi/gxf)  
    A partir de um post da comunidade Interrupt, este Quadro de Extensão GDB é uma biblioteca Python para facilitar a escrita de extensões GDB. Somos grandes fãs da API GDB Python na Memfault, então estamos felizes que projetos como o GFX existem! - François
    
-   [**StateSmith/StateSmith: Uma ferramenta de geração de código de máquina estatal adequada para metal nu, incorporado e muito mais.**](https://github.com/StateSmith/StateSmith)  
    um editor de máquina de estado finito com a capacidade de gerar código C que você pode incluir diretamente em seus projetos. (via Reddit /r/embedded). - François
    
-   [**tsoding/olive.c: Biblioteca gráfica 2D simples para C**](https://github.com/tsoding/olive.c)  
    Uma biblioteca gráfica C simples com 0 dependências que poderiam ser facilmente adaptadas para embutidos. - François
    
-   [**Joey Castillo Reinicia o Projeto Livro Aberto com um Raspberry Pi Pico-Powered Redesign - Hackster.io**](https://www.hackster.io/news/joey-castillo-reboots-the-open-book-project-with-a-raspberry-pi-pico-powered-redesign-8bfee0675637)  
    Um leitor de ebook de código aberto muito agradável que usa um Raspberry Pi Pico. -Noé
    

## Anúncios & Notícias[](https://interrupt.memfault.com/blog/september-2022-roundup#announcements--news)

-   [**Arm's Dev Summit agora é apenas on-line e livre**](https://www.arm.com/company/events/devsummit)  
    Eu vou estar falando no Arm Dev Summit deste ano falando sobre monitorar milhões de dispositivos remotamente, e Alvaro Prieto da Sofar Ocean estará falando sobre dispositivos depuração remotamente enquanto eles estão no mar. Tenho certeza que há outros, mas estes são os que eu conheço e podem confirmar que contêm conteúdo real para desenvolvedores.
    
-   [**Divulgando a publicação do Draft Ferrocene - O Blog AdaCore**](https://blog.adacore.com/announcing-publication-of-the-draft-ferrocene-language-specification)de Quentin Ochem  
    Ferrous Systems e Adacore lançaram suas especificações para rust certificada por segurança.
    

![](https://interrupt.memfault.com/img/author/tyler.jpg) [Tyler Hoffman](https://interrupt.memfault.com/authors/tyler)trabalhou nas equipes de software embarcadas em Pebble e Fitbit. Ele agora é um dos fundadores da[Memfault](https://memfault.com/).  
[](https://twitter.com/ty_hoff)[](https://www.linkedin.com/in/tyhoff/)[](https://github.com/tyhoff)
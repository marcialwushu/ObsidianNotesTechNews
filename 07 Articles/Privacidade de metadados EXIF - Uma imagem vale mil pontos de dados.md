---
link: https://www.comparitech.com/blog/vpn-privacy/exif-metadata-privacy/
author: {{author}}
published: {{published}}
tags: [{{tags:,}}]
date: July 10, 2022 (Sun)
---
# Highlights
{{highlights}}

---
# Privacidade de metadados EXIF - Uma imagem vale mil pontos de dados
## Privacidade de metadados EXIF: Uma imagem vale mil pontos de dados

As fotos que você compartilha online representam uma ameaça à sua privacidade?

@pabischoff 21 de outubro de 2021

Quando você tira uma foto digital com sua câmera ou telefone, ela armazena mais do que apenas os pixels e cores que compõem a imagem. Cada arquivo de imagem também contém metadados, que incluem detalhes que vão desde a data de criação e informações de direitos autorais até o local onde a foto foi tirada.

O mesmo vale para imagens modificadas com muitos programas de edição de fotos. Programas de edição de imagens geralmente adicionam metadados às imagens, incluindo datas de modificação, informações do sistema e alterações rastreadas.

[![metadados da caixa de fotos](https://cdn.comparitech.com/wp-content/uploads/2021/10/photobox-metadata.jpg)](https://cdn.comparitech.com/wp-content/uploads/2021/10/photobox-metadata.jpg)

Um exemplo de metadados EXIF armazenados com uma foto, incluindo as coordenadas GPS onde a foto foi tirada.

Metadados podem representar uma ameaça de privacidade para as pessoas que compartilham e postam fotos online. Embora algumas redes sociais e sites de armazenamento e compartilhamento de fotos esfreguem metadados de fotos enviadas, muitos não conseguem fazê-lo, dizem os pesquisadores da Comparitech, o que poderia permitir que os invasores coletassem informações pessoais a partir de imagens postadas online. Por exemplo, se alguém postar uma foto de férias com coordenadas GPS e um fuso de tempo nos metadados, um invasor pode facilmente encontrar quando e para onde viajou.

**Os metadados podem ser categorizados em três grandes categorias:**

-   Os metadados do sistema são gerados quando a imagem é armazenada (ou seja, quando uma foto é tirada ou as edições são salvas). Ele inclui critérios específicos de rotulagem, como a data e a hora em que a imagem foi criada e detalhes sobre a câmera e/ou software de edição usado
-   Metadados substantivos incluem o conteúdo do arquivo real, como alterações rastreadas em uma imagem editada
-   Os metadados incorporados incluem dados inseridos em um documento que normalmente não é visível, como fórmulas em uma planilha do Excel

Os metadados de imagem podem ser incorporados internamente em formatos de arquivo de imagem comuns, como JPEG e PNG. Esses dados de imagem geralmente são armazenados no Exif (formato de arquivo de imagem comercializável). Mas também pode existir fora do arquivo de imagem em um sistema de gerenciamento de ativos digitais (DAM). Estes são às vezes referidos como arquivos "sidecar", e são frequentemente armazenados no formato XMP.

**Metadados tem três casos de uso amplo:**

-   Descrevendo o conteúdo do arquivo, incluindo palavras-chave, nomes de pessoas retratadas e coordenadas de localização
-   Informações sobre direitos autorais incluem atribuição do criador, restrições de licenciamento, créditos e termos de uso
-   Os dados administrativos podem incluir a data de criação, a data de modificação, a localização e outros metadados do sistema mencionados acima.

## Quais serviços de compartilhamento de imagem esfregam metadados e quais não são?

Os pesquisadores da Comparitech analisaram as práticas de esfregamento de metadados de 12 serviços populares de armazenamento e compartilhamento de imagens on-line. Eles enviaram uma imagem da Mona Lisa carregada de metadados para cada um dos serviços. Após o upload, eles então baixaram a imagem de cada serviço respectivo para ver se os metadados permaneceram intactos ou não.

[![metadados imgbb](https://cdn.comparitech.com/wp-content/uploads/2021/10/gifyu-metadata-1024x670.jpg)](https://cdn.comparitech.com/wp-content/uploads/2021/10/gifyu-metadata.jpg)

Uma imagem enviada para imgbb, exibida em uma página da Web com seus metadados originais.

Let’s start with the most popular places to share images on the web. **Imgur, Facebook and Instagram all scrub all metadata** from photos upon upload. You don’t have to worry about leaking metadata when uploading images to these sites. Bear in mind, however, that even though users of those sites don’t have access to metadata, the sites themselves do.

**Flickr keeps all of the original metadata data** and even displays a lot of it on each photo’s web page.

**Photobox.co.uk** tags photos in the metadata comments section to indicate that uploaded images are compressed. The rest of the metadata is intact. It was the only service that actually added or modified data.

The remaining image sharing and storage services we examined didn’t remove or modify any metadata except for “date modified” timestamps:

-   Pasteboard.co
-   Turbmoimagehost.com
-   Linkpicture.com
-   8upload.com
-   Imgpile.com
-   Postimages.org
-   Imgbb.com
-   Imageupload.io
-   Gifyu

If you don’t want to expose EXIF metadata on those sites, you’ll have to scrub images beforehand. More on how to do that below.

## How you can be tracked using EXIF metadata: research examples

Comparitech researchers proved the sensitivity of image metadata by using publicly available images to track down image subjects and creators. (Note: we’ve scrubbed all of the following images of their original metadata).

[![exif metadata example](https://cdn.comparitech.com/wp-content/uploads/2021/10/unnamed-3-548x1024.jpg)](https://cdn.comparitech.com/wp-content/uploads/2021/10/unnamed-3.jpg)

Let’s start with a simple example. Using the GPS metadata in the above photo, we determined it was taken near Sørstranda, Norway.

[![exif metadata example 2](https://cdn.comparitech.com/wp-content/uploads/2021/10/unnamed-1.jpg)](https://cdn.comparitech.com/wp-content/uploads/2021/10/unnamed-1.jpg)

The next subject was a photo of a man’s face. Using the image metadata, reverse image search, and a bit of open-source intelligence (OSINT), researchers were able to identify him as a previous game-show contestant. They found his country, date of birth, wedding date, spouse’s name, Facebook profile, Twitter account, LinkedIn page, Instagram account, work experience, skills, education, and interests. Researchers were also able to identify and find info about the subject’s game-show teammates as well.

[![exif metadata example 3](https://cdn.comparitech.com/wp-content/uploads/2021/10/unnamed-2.jpg)](https://cdn.comparitech.com/wp-content/uploads/2021/10/unnamed-2.jpg)

Another subject was a passport-style headshot featuring a man in what appear to be military fatigues. Researchers were able to track down the image to a site with photos of the subject’s school graduation. Using the school name and graduation gallery, researchers retrieved the names of everyone in his graduating class. With the possibilities narrowed down, they found a man with a name similar to that of the image filename. Researchers went on to find the man’s Facebook and Instagram profiles. Using these images, they further discovered he was indeed a soldier. They learned his division and brigade, and info about his closest relatives.

[![exif metadados exemplo 4](https://cdn.comparitech.com/wp-content/uploads/2021/10/unnamed-768x1024.jpg)](https://cdn.comparitech.com/wp-content/uploads/2021/10/unnamed.jpg)

Por fim, pesquisadores identificaram um cidadão filipino usando uma foto sua postada em um site de compartilhamento de imagens. O sujeito está segurando a identificação com foto. Essas fotos são frequentemente usadas para verificar a identidade do sujeito em um serviço digital, como um banco online. Os pesquisadores puderam descobrir o país do assunto, data de nascimento, peso, altura, tipo sanguíneo, endereço, perfil do Facebook, emprego, educação, que ela teve recentemente Covid-19, e seu canal no Youtube.

## Metadados usados como prova judicial

Metadados de imagens e outros arquivos têm sido usados como evidência em tribunais de justiça e investigações policiais, demonstrando o valor de metadados de uma perspectiva de privacidade. Aqui estão alguns exemplos proeminentes:

-   Em 2016, dois estudantes de Harvard usaram coordenadas GPS armazenadas nos metadados de fotos postadas na dark web para identificar [traficantes de drogas 229 traficantes](https://www.bitdefender.com/blog/hotforsecurity/229-drug-dealers-caught-after-failing-to-remove-photo-exif-metadata). Os traficantes de drogas da Dark Web frequentemente postam imagens de seus produtos online para ajudar a provar sua credibilidade, mas muitas vezes esquecem de esfregar dados exif de antemão.
-   Em 2017, um funcionário da Bio-Rad Laboratories [entrou com uma ação contra](https://www.law.com/therecorder/almID/1202778583134/Ousted-BioRad-GC-Wins-Whistleblower-Case/?mcode=0&curindex=0&curpage=ALL/&slreturn=20210913162413) seu empregador alegando que ele foi demitido por contar às autoridades sobre um possível suborno na China. Uma revisão de desempenho com um metadados datado depois que ele foi demitido serviu como prova no caso, resultando em um pagamento maior por violar leis contra demissão de denunciantes. Este é o maior pagamento vinculado a metadados até agora em US $ 10,8 milhões em danos.
-   Em 2015, um juiz [descartou um caso](https://ncavf.com/blog/wife-claims-years-of-abuse-digital-image-metadata-proves-was-all-lies/) em que uma mulher acusou seu cônjuge de abuso físico. O autor da ação forneceu várias fotos como evidência de abuso, mas os metadados indicaram a data em que a esposa havia afirmado que o abuso ocorreu três meses após as fotos serem tiradas.
-   A empresa de perícia digital Legility publicou um [estudo de caso](https://www.inventus.com/hubfs/Legility_Case%20Study_Digital%20Forensics%20-%20Using%20Metadata%20to%20Prove%20a%20Case.pdf) (PDF) descrevendo um processo que investigou. Nesse caso, uma empresa de saúde adquiriu outro negócio. Funcionários da empresa original partiram para abrir sua própria empresa. A empresa agora adquirida processou a nova empresa, alegando que ela roubou funcionários e roubou segredos comerciais e documentos proprietários, incluindo listas de clientes. Usando os metadados desses documentos como prova de quando os documentos foram copiados e transferidos, a empresa adquirida foi recompensada em 7 milhões de dólares (PIB 5,1 milhões de libras).

## Como remover metadados de imagens

Câmeras e aplicativos de câmera variam bastante, mas muitos deles têm a opção de desligar ou limitar a geração de metadados. Verifique as configurações da câmera ou do aplicativo.

A maioria das câmeras e programas de edição de imagens armazenam metadados de imagem no formato EXIF. Você pode ser capaz de editar dados EXIF na saída de imagens através de sua câmera ou aplicativo de edição de fotos.

Alguns programas são especificamente projetados para trabalhar com metadados. [ExifTool](https://exiftool.org/) e [Image Scrubber](https://everestpipkin.github.io/image-scrubber/) são duas ótimas opções de código aberto.

**O Windows 10 vem com uma opção embutida para remover metadados**. No entanto, isso só removerá metadados que o Windows 10 entende, o que significa que pode deixar alguns metadados para trás. Ainda assim, deve pelo menos ajudar a minimizar as informações armazenadas nas imagens. Se você é um usuário de PC, basta seguir estes passos:

1.  Clique com o botão direito do mouse no arquivo de imagem e selecione **Propriedades** para abrir uma nova janela
2.  Clique na guia **Detalhes** na parte superior[![janelas remover metadados 2](https://cdn.comparitech.com/wp-content/uploads/2021/10/windows-remove-metadata-2.jpg)](https://cdn.comparitech.com/wp-content/uploads/2021/10/windows-remove-metadata-2.jpg)
3.  Clique no link que diz **Remover propriedades e informações pessoais** na parte inferior. Outra nova janela aparecerá.[![janelas remover metadados 3](https://cdn.comparitech.com/wp-content/uploads/2021/10/windows-remove-metadata-3.jpg)](https://cdn.comparitech.com/wp-content/uploads/2021/10/windows-remove-metadata-3.jpg)
4.  Na janela **Remover propriedades**, selecione **Remover as seguintes propriedades deste arquivo:**
5.  Clique **em Selecionar Tudo**, então **OK**
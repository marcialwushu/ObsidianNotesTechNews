---
link: https://github.com/bacen/pix-dict-api/issues/6
author: morellibmv
published: 2020-08-27T14:46:00
tags: []
---
# Highlights


---
# Geração de Arquivo CID com status AVAILABLE mas ao tentar fazer download do arquivo, retorna 404.
Solicitamos a geração de arquivos CID. Recebemos o status AVAILABLE para o arquivo abaixo: [https://arq-h.pi.rsfn.net.br/api/v1/download/01181521/cidsetfile/01181521_EMAIL_14241_2020-08-27T17:01:08.273Z.txt](https://arq-h.pi.rsfn.net.br/api/v1/download/01181521/cidsetfile/01181521_EMAIL_14241_2020-08-27T17:01:08.273Z.txt)

Segue o XML de retorno:

```
<GetCidSetFileResponse><ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#"><ds:SignedInfo><ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/><ds:SignatureMethod Algorithm="http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"/><ds:Reference URI="#key-info-id"><ds:Transforms><ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/></ds:Transforms><ds:DigestMethod Algorithm="http://www.w3.org/2001/04/xmlenc#sha256"/><ds:DigestValue>pHDbsKklpORCx1ABvvlCOZIg/+2QjO90lesGqdGitbE=</ds:DigestValue></ds:Reference><ds:Reference URI=""><ds:Transforms><ds:Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/><ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/></ds:Transforms><ds:DigestMethod Algorithm="http://www.w3.org/2001/04/xmlenc#sha256"/><ds:DigestValue>Fknk1JyQD/Pz0l7Mw5DDk7NtOUolq1VF4i9yDHQQ4O4=</ds:DigestValue></ds:Reference></ds:SignedInfo><ds:SignatureValue>k8c/w0vI8O8Kufy0QUeD7DJywfIyrGKuPwI/m2AUpFThZQssZWCX0scZazqC92zrXiBwSJOS6zEl
rZ+Z7/Al8+lqKgFCQ0n2RDu9L6J4wHDD0YMGtsHJSJZhXLiyOg2gCi70Lc+OUVKe5LgSwSjqIdgf
YTuIQH0ksQBcugzKInFyr4NvH4LW1EyPzlIDcpBBZyKI8dUvb98VCiEKD2fFKaMaAQnj4dukylBS
Hxubpi2nEmDNLG+BxHb9GjOVX4kBX+W7Gml4360hZtH+yC8CWpp20JXjLsCQMJYjrceBNjDAIbla
epcBKslV2YMGeuDzCXOSXsjbADNzg0JEmm0QEQ==</ds:SignatureValue><ds:KeyInfo Id="key-info-id"><ds:X509Data><ds:X509IssuerSerial><ds:X509IssuerName>CN=Autoridade Certificadora do SERPRO Final SSL, OU=Servico Federal de Processamento de Dados - SERPRO, OU=CSPB-1, O=ICP-Brasil, C=BR</ds:X509IssuerName><ds:X509SerialNumber>66906355272994040667436154809</ds:X509SerialNumber></ds:X509IssuerSerial></ds:X509Data></ds:KeyInfo></ds:Signature><CidSetFile><Id>14241</Id><Status>AVAILABLE</Status><Participant>01181521</Participant><KeyType>EMAIL</KeyType><RequestTime>2020-08-27T17:01:08.256Z</RequestTime><CreationTime>2020-08-27T17:01:08.734Z</CreationTime><Url>https://arq-h.pi.rsfn.net.br/api/v1/download/01181521/cidsetfile/01181521_EMAIL_14241_2020-08-27T17:01:08.273Z.txt</Url><Bytes>12090</Bytes><Sha256>9748064e9f7d47d54f4ae4a0fcf2d519c686204a056d5b60303c274d1bba0f06</Sha256></CidSetFile></GetCidSetFileResponse>
```

Segue o retorno para o GET da URL:

```
<?xml version="1.0" encoding="UTF-8"?>
<problem xmlns="urn:ietf:rfc:7807">
    <type>https://icom.pi.rsfn.net.br/api/v1/error/notFound</type>
    <title>Não encontrado</title>
</problem>
```
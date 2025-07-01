---
title: 'Erro de cURL 60: certificado SSL expirado'
description: 'Este artigo mostra como verificar quando a última vez que uma ramificação foi implantada depois de receber um erro de cURL 60: o certificado SSL expirou nas ramificações Principal ou de Integração no Adobe Commerce na infraestrutura em nuvem.'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: dcaae51408534b82181b268f60905b123e240900
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Erro de cURL 60: certificado SSL expirado

Este artigo mostra como verificar quando a última vez que uma ramificação foi implantada depois de receber um `cURL error 60`: [!DNL SSL certificate] expirou nas ramificações [!DNL Master] ou [!DNL Integration] no Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Causa

O [!DNL SSL certificates] nessas ramificações é válido por apenas 30 dias, e a ramificação pode não ter sido reimplantada por mais de 30 dias.

O erro será semelhante a este:

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

>[!NOTE]
>
>Esses certificados não são assinados por autoridades de certificação (CAs) externas conhecidas como [!DNL Let's Encrypt] ou [!DNL DigiCert]. Eles são gerenciados pela plataforma Adobe para fins de teste e desenvolvimento e podem não ser confiáveis por padrão em navegadores ou curl, a menos que você confie explicitamente na raiz que emite o certificado.

## Solução

Verifique quando a última vez que a ramificação foi implantada. Se o limite de 30 dias for ultrapassado, reimplante a ramificação.

Dois métodos para verificar quando a última implantação foi executada:

* [Método 1: Use [!DNL magento-cloud] CLI](#meth2).
* [Método 2: abrir  [!DNL Project URL]](#meth3).

Se a implantação for concluída com êxito, o [!DNL SSL certificate] será renovado automaticamente.

Se a implantação falhar e você precisar de ajuda para resolvê-la, [envie um tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=pt-BR#submit-ticket).

### Método 1: usar a CLI do [!DNL magento-cloud] {#meth2}

Executar este comando: `magento-cloud activity:list --type=environment.push`

### Método 2: abrir o [!DNL Project URL] {#meth3}

Vá para, por exemplo: `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`, e verifique quando a última implantação foi executada.

## Leitura relacionada

Em nossa documentação do desenvolvedor:

* [API do Cloud Manager: SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Configurar o Fastly: Provisionar certificados SSL/TLS](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

Em nossa base de conhecimento de suporte:

* [Informações de expiração do certificado SSL personalizado](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html?lang=pt-BR)
* [Certificados SSL (TLS) para Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html?lang=pt-BR)

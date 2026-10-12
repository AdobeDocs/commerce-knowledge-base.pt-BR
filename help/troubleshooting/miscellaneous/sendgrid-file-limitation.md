---
title: '[!DNL SendGrid] limitação de arquivos para a Adobe Commerce Cloud'
description: Este artigo fornece uma solução alternativa para a limitação [!DNL SendGrid] do Adobe Commerce na infraestrutura em nuvem.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%
---
# [!DNL SendGrid] limitação para a Adobe Commerce Cloud

Este artigo fornece algumas soluções alternativas para a limitação do [!DNL SendGrid] para a infraestrutura do Adobe Commerce na nuvem.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Problema

Você tenta enviar anexos grandes em emails e vê estes erros de log:

Em `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

Em `/var/log/exception.log`

Produção:

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Estágios:

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Estágios2:

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Causa

[!DNL SendGrid] tem uma limitação de sistema de 30 Mb para email. É recomendável não usar anexos com mais de 10 Mb. Consulte [Enviando anexos](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) na documentação do SendGrid para obter mais informações.

## Solução alternativa

* Não use anexos com mais de 6Mb ou 10Mb.
* Considere o uso de um servidor SMTP remoto em sua instância do Adobe Commerce. Para ver as etapas, consulte [Configurar comunicações por email](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html?lang=pt-BR) em nosso Guia de Sistemas de Administração.
* Reconfigure o servidor para que os arquivos possam ser salvos no módulo e, em seguida, anexe o link aos arquivos nos emails.

## Leitura relacionada

* [[!DNL SendGrid] serviço de email](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html?lang=pt-BR) em nosso Guia de Infraestrutura do Commerce na Nuvem.

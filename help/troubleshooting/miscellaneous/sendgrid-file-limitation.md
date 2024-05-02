---
title: '[!DNL SendGrid] limitação de arquivos para o Adobe Commerce Cloud'
description: Este artigo fornece uma solução alternativa para o  [!DNL SendGrid] limitação do Adobe Commerce na infraestrutura em nuvem.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# [!DNL SendGrid] limitação para o Adobe Commerce Cloud

Este artigo fornece algumas soluções alternativas para o [!DNL SendGrid] limitação do Adobe Commerce na infraestrutura na nuvem.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões compatíveis](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Problema

Você tenta enviar anexos grandes em emails e vê estes erros de log:

Entrada `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

Entrada `/var/log/exception.log`

Produção:

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Estágios:

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Estágios2:

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Causa

[!DNL SendGrid] O tem uma limitação de sistema de 30 Mb para email. É recomendável não usar anexos com mais de 10 Mb. Consulte [Enviando anexos](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) na documentação do SendGrid para obter mais informações.

## Solução alternativa

* Não use anexos com mais de 6Mb ou 10Mb.
* Considere o uso de um servidor SMTP remoto em sua instância do Adobe Commerce. Para obter etapas, consulte [Configurar comunicações por email](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html) em nosso Guia de sistemas de administração.
* Reconfigure o servidor para que os arquivos possam ser salvos no módulo e, em seguida, anexe o link aos arquivos nos emails.

## Leitura relacionada

* [[!DNL SendGrid] serviço de e-mail](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html) em nosso Guia de infraestrutura do Commerce na nuvem.

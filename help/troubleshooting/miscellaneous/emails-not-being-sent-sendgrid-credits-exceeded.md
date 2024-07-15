---
title: Emails não enviados quando os créditos SendGrid são excedidos no Adobe Commerce
description: Este artigo fornece uma solução quando seus emails não estão sendo enviados porque você excedeu o limite de créditos do SendGrid no Adobe Commerce.
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: e04bb0b37e795cae3380e1110e6db95be12036b0
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Emails não enviados quando os créditos SendGrid são excedidos no Adobe Commerce

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Problema

Os créditos do SendGrid se referem ao número de emails permitidos que podem ser enviados. Somente 12.000 emails podem ser enviados por mês das ramificações de integração e Armazenamento temporário. Os créditos são renovados no início do mês, portanto, se você ficar sem créditos, terá que aguardar a renovação.

Não há limites rígidos para o número de emails que podem ser enviados em produção, desde que a Reputação do remetente esteja acima de 95%. A reputação é afetada pelo número de emails devolvidos/rejeitados e se os registros de spam baseados em DNS sinalizaram seu domínio como uma possível fonte de spam. Na produção, um total de 12.000 emails são alocados por dia, mas esse número pode ser estendido com base no número médio de emails enviados nos cinco dias anteriores.

## Como verificar se seus créditos foram excedidos:

Arquitetura do plano Pro da infraestrutura na nuvem do Adobe Commerce: verifique o `/var/log/mail.log` - você poderá ver uma mensagem como esta:

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## Causa

Há limites para o número de emails permitidos que podem ser enviados.

## Solução

* Se você vir esta mensagem no ambiente de Produção, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), forneça a mensagem acima e solicite o aumento dos créditos.
* Se você não vir esta mensagem ou se estiver na arquitetura de plano inicial do Adobe Commerce na infraestrutura em nuvem, também [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e mencione que o arquivo `mail.log` não indica que os créditos foram excedidos.

## Leitura relacionada

* [SendGrid](https://devdocs.magento.com/cloud/project/sendgrid.html) em nossa documentação do desenvolvedor.

---
title: Dicas de testes de terceiros para o Adobe Commerce na infraestrutura em nuvem
description: Este artigo fornece opções para compartilhar o acesso com terceiros para teste/validação quando você tiver um problema com uma extensão do Adobe Commerce na infraestrutura em nuvem.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Dicas de testes de terceiros para o Adobe Commerce na infraestrutura em nuvem

Este artigo fornece opções para compartilhar o acesso com terceiros para teste/validação quando você tiver um problema com uma extensão do Adobe Commerce na infraestrutura em nuvem.
Procedimentos e requisitos internos adequados de segurança de dados devem ser seguidos por você ao decidir a maneira de fornecer acesso a terceiros.

## Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Quais ambientes usar para testes

Dependendo dos seus padrões internos de segurança, você pode optar pela solução de problemas de terceiros em um ambiente local. Se o problema não puder ser reproduzido localmente, talvez você queira fornecer acesso ao seu ambiente de nuvem. Se você optar por fazer isso, certifique-se de trabalhar de acordo com seus padrões internos de segurança. Se estiver fornecendo acesso a qualquer um de seus ambientes de nuvem, verifique se terceiros sabem o que pode ser feito e qual aprovação é necessária para tarefas como somente replicação ou permissão de alterações de código. Isso é especialmente importante para ambientes de produção.

## Fornecer a terceiros acesso e dados

* Forneça acesso de terceiros ao ambiente de nuvem. Artigos relacionados:

   * [Guia do Usuário da Central de Ajuda do Adobe Commerce > ACESSO COMPARTILHADO: CONCEDER PRIVILÉGIOS PARA QUE OUTROS USUÁRIOS ACESSEM SUA CONTA](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access) em nossa base de dados de conhecimento de suporte.
   * [Compartilhando sua conta da Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/start/commerce-account/commerce-account-share) em nosso guia do usuário.

* Crie um despejo de banco de dados (ou conceda acesso a fornecedor de terceiros para fazer isso). Isso pode ser feito usando a CLI ou no Commerce Admin. Esse despejo de DB ofuscará os dados do cliente, de modo que tudo o que eles obtêm é código e SKUs de produto etc., sem dados de propriedade/cliente. Para referência, use o [Compartilhamento de sua conta da Commerce] (/help/how-to/general/create-database-dump-on-cloud.md) em nossa knowledge base de suporte.
* Quando o teste for concluído, revogue o acesso compartilhado ao seu ambiente de nuvem, conforme descrito no [Guia do Usuário da Central de Ajuda da Adobe Commerce > Revogar (excluir acesso compartilhado)](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access) em nossa base de dados de conhecimento de suporte.

## Prática recomendada de teste

A prática padrão é solucionar problemas em um ambiente local. Se o problema não puder ser reproduzido localmente, vá para Preparo. Talvez o terceiro precise verificar a Produção. Certifique-se de que terceiros estejam cientes de que só devem tentar reproduzir o problema na Produção e no Armazenamento temporário e não devem fazer alterações no código. Além disso, se precisarem fazer alterações no código, primeiro deverão obter sua permissão.

## Leitura relacionada

* [Práticas recomendadas para usar extensões de terceiros no Adobe Commerce](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) em nossa base de dados de conhecimento de suporte.

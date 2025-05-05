---
title: Sincronizar dados e arquivos da produção para preparo ou preparo para integração
description: Este artigo explica como sincronizar seu ambiente de produção para Armazenamento temporário na Adobe Commerce na infraestrutura em nuvem. Isso não é possível.
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Sincronizar dados e arquivos da produção para preparo ou preparo para integração

Este artigo explica como sincronizar seu ambiente de produção para Armazenamento temporário na Adobe Commerce na infraestrutura em nuvem. Isso não é possível por meio da interface do usuário ou da CLI Magento-cloud.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.3.x, 2.4.x

## Para sincronizar dados de um ambiente para outro

Para sincronizar os dados, você deve despejar manualmente o banco de dados do ambiente de origem. Para transferir dados para outro ambiente, carregue o despejo de origem no ambiente de destino e importe-o. Para obter mais informações, consulte [Importar código do Adobe Commerce para um projeto na nuvem > Importar banco de dados do Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) na documentação do desenvolvedor.

Para a arquitetura de plano Pro da infraestrutura em nuvem do Adobe Commerce, você também pode sincronizar do armazenamento temporário e da produção para a sua ramificação mestre de integração. Essa sincronização extrai e envia apenas código, não dados. Para sincronizar dados, você precisará despejar os dados do banco de dados e enviá-los para outro banco de dados do ambiente.

>[!WARNING]
>
>A sincronização do banco de dados não pode ser feita nos clusters Pro Staging e Production.

## Para sincronizar arquivos de um ambiente para outro

Para sincronizar arquivos de um ambiente para outro, use o comando `rsync`. Para obter mais informações, consulte [Implantar código e migrar arquivos estáticos e dados > Migrar arquivos usando rsync](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production#migrate-files-using-rsync) na documentação do desenvolvedor.

>[!NOTE]
>
>Se você quiser sincronizar o código da integração para o armazenamento temporário, é necessário fazer isso a partir da ramificação de integração. Para ver as etapas, consulte [Sincronizar do pai do ambiente](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment) na documentação do desenvolvedor.

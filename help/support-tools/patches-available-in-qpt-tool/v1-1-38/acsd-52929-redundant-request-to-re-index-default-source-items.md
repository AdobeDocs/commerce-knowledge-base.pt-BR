---
title: 'ACSD-52929: solicitação redundante para reindexar itens de origem padrão'
description: Aplique o patch ACSD-52929 para corrigir o problema do Adobe Commerce em que há uma solicitação redundante para reindexar os itens de origem padrão quando o indexador de inventário estiver configurado no modo assíncrono.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 978fe0d0-3917-4ba2-94bb-01c607a825cc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52929: solicitação redundante para reindexar itens de origem padrão

O patch ACSD-52929 corrige o problema de redundância de solicitações para reindexar itens de origem padrão quando o indexador de inventário é configurado no modo assíncrono. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.38 está instalado. A ID do patch é ACSD-52929. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Há uma redundância de solicitações para reindexar itens de origem padrão quando o indexador de inventário é configurado no modo assíncrono.

<u>Etapas a serem reproduzidas</u>:

1. Configurar [!DNL RabbitMQ].
1. Habilite a estratégia de reindexação assíncrona indo até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** e defina **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Crie uma origem de inventário personalizada.
1. Faça logon no painel [!DNL RabbitMQ] e vá para a guia filas.
1. Verifique a fila `inventory.indexer.sourceItem` e certifique-se de que ela tenha zero mensagens.
1. Abra um produto simples no back-end, adicione *[!UICONTROL stock only]* à fonte personalizada e salve o produto.
1. Carregue a fila `inventory.indexer.sourceItem` no painel [!DNL RabbitMQ] e verifique as mensagens.

<u>Resultados esperados</u>:

Há apenas uma mensagem na fila para a fonte personalizada.

<u>Resultados reais</u>:

Duas mensagens são mostradas na fila: uma para a origem padrão e outra para a origem personalizada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].

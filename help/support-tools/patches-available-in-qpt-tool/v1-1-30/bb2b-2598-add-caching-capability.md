---
title: "BB2B-2598: Adiciona o recurso de armazenamento em cache a storeConfig, moeda, país, países, queries GraphQl availableStores"
description: Aplique o patch BB2B-2598 para adicionar o recurso de armazenamento em cache às consultas storeConfig, moeda, país, países e GraphQl availableStores.
exl-id: 37551954-d721-4f3a-b237-cd795f715a5f
feature: B2B, GraphQL, Cache
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# BB2B-2598: Adiciona recurso de cache ao `storeConfig`, `currency`, `country`, `countries`, e `availableStores` Consultas GraphQl

O patch BB2B-2598 adiciona a capacidade de armazenamento em cache para `storeConfig`, `currency`, `country`, `countries`, e `availableStores` Consultas GraphQl. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.30 está instalado. A ID do patch é BB2B-2598. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7-beta1.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

`availableStores`, `countries`, `country`, `currency`, `storeConfig`, e `customAttributeMetadata` As consultas do GraphQL não podem ser armazenadas em cache.

<u>Pré-requisitos</u>:

* O servidor aponta para [!DNL Varnish] proxy para o back-end do Adobe Commerce.
* Configuração `system/full_page_cache/caching_application` está definida como *2* ([!DNL Varnish]) ou acesse o Administrador do Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > e defina-o como [!DNL Varnish].

Após a aplicação do patch, execute as seguintes etapas para garantir que o recurso de cache esteja disponível:

1. Enviar `GET` para qualquer uma das consultas do GraphQL listadas acima, usando quaisquer campos arbitrários.
1. Reenviar a solicitação sem qualquer alteração. Você notará que é muito mais rápido. Observe que a solicitação não é enviada para o backend, mas é completamente tratada pelo [!DNL Varnish] como uma ocorrência de cache.
1. Se for necessária mais prova, comente o cancelamento da `X-Magento-Debug` cabeçalho presente em nosso [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227)e reinicie o [!DNL Varnish] e execute novamente as etapas acima.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

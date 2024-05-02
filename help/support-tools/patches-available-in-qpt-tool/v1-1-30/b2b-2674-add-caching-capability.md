---
title: "B2B-2674: adiciona o recurso de armazenamento em cache à consulta de GraphQL customAttributeMetadata"
description: Aplique o patch B2B-2674 para adicionar o recurso de cache à consulta de GraphQL customAttributeMetadata.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: a4efb268-f811-41f2-a788-a8cfc3016f61
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# B2B-2674: Adiciona o recurso de cache ao `customAttributeMetadata` consulta do GraphQL

O patch B2B-2674 adiciona o recurso de cache ao `customAttributeMetadata` consultas do GraphQL. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.30 está instalado. A ID do patch é B2B-2674. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7-beta1.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

`customAttributeMetadata` A consulta do GraphQL não pode ser armazenada em cache.

<u>Pré-requisitos</u>:

* O servidor aponta para [!DNL Varnish] proxy para o back-end do Adobe Commerce.
* Configuração `system/full_page_cache/caching_application` está definida como *2* ([!DNL Varnish]) ou acesse o Administrador do Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > e defina-o como [!DNL Varnish].

Após a aplicação do patch, execute as seguintes etapas para garantir que o recurso de cache esteja disponível:

1. Enviar `GET` para a consulta do GraphQL listada acima, usando quaisquer campos arbitrários.
1. Reenviar a solicitação sem qualquer alteração. Você notará que é muito mais rápido. Observe que a solicitação não é enviada para o backend, mas é completamente tratada pelo [!DNL Varnish] como uma ocorrência de cache.
1. Se for necessária mais prova, comente o cancelamento da `X-Magento-Debug` cabeçalho presente em nosso [VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239)e reinicie o [!DNL Varnish] e execute novamente as etapas acima.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

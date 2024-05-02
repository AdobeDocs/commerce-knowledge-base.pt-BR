---
title: '[!DNL ACSD-47280]: Desativar catálogo compartilhado fornece resultados de pesquisa de produto errados'
description: Aplique o [!DNL ACSD-47280] correção para corrigir a exibição dos resultados de pesquisa corretos quando o recurso de catálogo compartilhado está desativado.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: a desativação do catálogo compartilhado retorna resultados incorretos da pesquisa de produto

A variável [!DNL ACSD-47280] correção corrige a exibição dos resultados de pesquisa corretos quando a variável [!DNL shared catalog] recurso está desativado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.22 está instalado. A variável [!DNL patch ID] é [!DNL ACSD-47280]. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use o [!DNL patch ID] como uma palavra-chave de pesquisa para localizar o patch.

## Problema

Desativando [!DNL shared catalog] fornece resultados incorretos da pesquisa de produtos.

<u>Pré-requisitos</u>:

* [!DNL B2B] módulos instalados

<u>Etapas a serem reproduzidas</u>:

1. Crie um segundo site.
1. Atribua um produto ao segundo site.
1. Verifique os produtos no **segundo site** usar [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Ativar **[!UICONTROL Shared Catalog]** no padrão [!DNL scope].
1. A variável [!DNL GraphQL] não mostra mais nenhum produto para o segundo site, que é o resultado correto.
1. Vá para a [!DNL scope] do segundo site e desativar **[!UICONTROL Company]**.

<u>Resultados esperados</u>:

A variável [!DNL GraphQL] ainda deve mostrar os produtos para o segundo site.

<u>Resultados reais</u>:

A variável [!DNL GraphQL] não mostra nenhum produto para o segundo site.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

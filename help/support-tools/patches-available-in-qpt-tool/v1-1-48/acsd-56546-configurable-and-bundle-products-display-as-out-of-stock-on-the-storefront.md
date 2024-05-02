---
title: "ACSD-56546: os produtos configuráveis e empacotados são exibidos como esgotados na loja"
description: Aplique o patch ACSD-56546 para corrigir o problema do Adobe Commerce em que os produtos configuráveis e empacotados são exibidos como esgotados na loja quando o *[!UICONTROL Display Out of Stock Products]* a opção de configuração está desativada.
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546: os produtos configuráveis e empacotados são exibidos como esgotados na loja

O patch ACSD-56546 corrige o problema em que os produtos configuráveis e empacotados são exibidos como esgotados na loja. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.48 está instalado. A ID do patch é ACSD-56546. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos configuráveis e empacotados são exibidos como indisponíveis na loja quando *[!UICONTROL Display Out of Stock Products]* está desabilitada.

<u>Etapas a serem reproduzidas</u>:

1. Defina o **[!UICONTROL Display Out of Stock Products]** opção para *Não*.
1. Crie um site, uma loja e uma loja.
1. Crie uma fonte e um estoque e atribua-o ao segundo site.
1. Criar um *produto configurável* com dois produtos secundários. Atribua os produtos secundários a fontes e sites.
1. Atualizar o primeiro produto filho a ter *qty=0* em ambas as fontes.
1. Atualize o segundo produto filho e desative-o no segundo site.
1. Fazer um reindexação completo.
1. Verifique a categoria que contém o produto configurável no segundo site.

<u>Resultados esperados</u>:

Os produtos configuráveis esgotados não estão visíveis na loja.

<u>Resultados reais</u>:

Os produtos configuráveis esgotados estão visíveis na loja mesmo quando a variável *[!UICONTROL Display Out of Stock Products]* está desabilitada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

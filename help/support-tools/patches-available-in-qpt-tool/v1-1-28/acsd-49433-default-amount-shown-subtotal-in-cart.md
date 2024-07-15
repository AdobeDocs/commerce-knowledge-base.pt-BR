---
title: "ACSD-49433: Valor padrão mostrado como subtotal no carrinho para cartão-presente'"
description: Aplique o patch ACSD-49433 para corrigir o problema do Adobe Commerce em que o valor padrão é mostrado como subtotal no carrinho para cartão-presente com um valor aberto.
exl-id: e2a887bb-c15a-43a6-a145-b295deef399b
feature: Admin Workspace, Gift, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-49433: Valor padrão mostrado como subtotal no carrinho para cartão-presente

O patch ACSD-49433 corrige o problema em que o valor padrão é mostrado como subtotal no carrinho para o cartão-presente com um valor aberto. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 está instalado. A ID do patch é ACSD-49433. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O valor padrão é mostrado como subtotal no carrinho para o cartão-presente com um valor aberto.

<u>Etapas a serem reproduzidas</u>:

1. Crie um cartão-presente.
1. Verifique se o valor aberto está definido como *[!UICONTROL Yes]* (entre US$ 50 e US$ 500).
1. Vá para o produto [!UICONTROL Gift Card] na loja e escolha outro valor no menu suspenso.
1. Especifique $100 no valor em USD.
1. Preencha outros campos e adicione-os ao carrinho.
1. Vá até o minicarrinho ou a página do carrinho.

<u>Resultados esperados</u>:

O subtotal mostra a quantidade inserida pelo usuário.

<u>Resultados reais</u>:

O subtotal mostra o valor padrão do vale-presente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

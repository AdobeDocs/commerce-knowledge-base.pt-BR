---
title: "ACSD-46581: O total de impostos estimado não é atualizado após selecionar um país no carrinho de compras"
description: Aplique o patch ACSD-46581 para resolver o problema do Adobe Commerce, em que a alíquota do imposto não é atualizada após trocar o país no carrinho de compras.
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581: O total de imposto estimado não é atualizado após selecionar um país no carrinho de compras

Este patch ACSD-46581 resolve o problema em que a alíquota do imposto não é atualizada depois de trocar o país no carrinho de compras. Ele é atualizado somente após selecionar o método de envio. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.21 está instalado. A ID do patch é ACSD-46581. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.1-p1

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A alíquota do imposto não é atualizada depois de alternar o país no carrinho de compras.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Adobe Commerce, acesse **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Criar uma nova alíquota para **[!UICONTROL Country]** = _Estados Unidos_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8,25_.
1. Criar uma nova alíquota para **[!UICONTROL Country]** = _Índia_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Crie uma regra de imposto com alíquotas de imposto para os EUA e a Índia.
1. Ir para **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** e ativar mais de um método de envio (_Taxa única_ e _Envio gratuito_ por exemplo).
1. Crie um produto simples com o **[!UICONTROL Taxable Goods]** classe de imposto.
1. Adicione o produto ao carrinho na loja.
1. Abra o carrinho de compras e verifique o valor do imposto.
1. As configurações de imposto padrão dos Estados Unidos são aplicadas e o imposto é calculado com base em uma taxa de 8,25%.
1. Mude o país para a Índia.

<u>Resultados esperados</u>:

O valor do imposto mudou para 10% quando o país foi transferido para a Índia.

<u>Resultados reais</u>:

O valor do imposto permanece o mesmo na seção total do carrinho de compras.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

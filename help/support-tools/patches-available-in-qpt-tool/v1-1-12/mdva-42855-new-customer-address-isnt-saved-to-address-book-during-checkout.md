---
title: "MDVA-42855: O novo endereço do cliente não é salvo no catálogo de endereços durante a finalização da compra"
description: O patch MDVA-42855 corrige o problema em que o novo endereço do cliente não é salvo no catálogo de endereços durante a finalização da compra. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-42855. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 37fc51f4-773e-4bef-9fb1-e6629562b94a
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-42855: O novo endereço do cliente não é salvo no catálogo de endereços durante a finalização da compra

O patch MDVA-42855 corrige o problema em que o novo endereço do cliente não é salvo no catálogo de endereços durante a finalização da compra. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-42855. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O novo endereço do cliente não é salvo no catálogo de endereços durante a finalização da compra.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma conta de cliente e atualize o endereço padrão de entrega e cobrança.
1. Adicione um produto ao carrinho e navegue até a página de check-out.
1. Ao enviar, clique em **+ Novo Endereço**.
1. Digite seu novo endereço e mantenha marcada a caixa de seleção **Salvar no Catálogo de Endereços**.
1. No Pagamento, marque a caixa de seleção **Meus endereços de cobrança e de entrega são iguais**.
1. Coloque o pedido.
1. Verifique o catálogo de endereços.

<u>Resultados esperados</u>:

O novo endereço de entrega é salvo no catálogo de endereços.

<u>Resultados reais</u>:

O novo endereço de entrega não é salvo no catálogo de endereços.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

---
title: "MDVA-37592: A classificação por preço não funciona para produtos com preço zero"
description: O patch do Adobe Commerce MDVA-37592 resolve o problema em que a classificação por preço não funciona corretamente para produtos com preço zero atribuído a um catálogo compartilhado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 está instalada. A ID do patch é MDVA-37592. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592: A classificação por preço não funciona para produtos com preço zero

O patch do Adobe Commerce MDVA-37592 resolve o problema em que a classificação por preço não funciona corretamente para produtos com preço zero atribuído a um catálogo compartilhado. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.0 está instalado. A ID do patch é MDVA-37592. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce em nossa arquitetura de nuvem 2.4.0-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os tipos de implantação) 2.3.6-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A classificação por preço não funciona corretamente para produtos com preço zero atribuído a um catálogo compartilhado.

<u>Pré-requisitos</u>:

B2B está instalado.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar catálogo compartilhado.
1. Crie quatro produtos com os preços a seguir e atribua-os a uma categoria - US$ 50, US$ 60, US$ 70 e US$ 80.
1. Crie um catálogo compartilhado com os produtos acima.
1. Defina o preço personalizado como zero para o produto com um preço de US$ 70.
1. Agora, crie um usuário da empresa e atribua-o ao catálogo compartilhado recém-criado.
1. Faça logon usando a conta da empresa e navegue até a categoria à qual os produtos estão atribuídos.
1. Tente classificar por preço.

<u>Resultados esperados</u>:

O produto com preço zero é classificado corretamente.

<u>Resultados reais</u>:

O produto com preço zero NÃO está classificado corretamente. Em vez disso, é classificado de acordo com o preço original.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

* Adobe Commerce no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce em nossa arquitetura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.

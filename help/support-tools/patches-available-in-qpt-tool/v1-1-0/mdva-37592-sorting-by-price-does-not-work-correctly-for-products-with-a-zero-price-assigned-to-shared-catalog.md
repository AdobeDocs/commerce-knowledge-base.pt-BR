---
title: 'MDVA-37592: A classificação por preço não funciona para produtos com preço zero'
description: O patch do Adobe Commerce MDVA-37592 resolve o problema em que a classificação por preço não funciona corretamente para produtos com preço zero atribuído a um catálogo compartilhado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 está instalada. A ID do patch é MDVA-37592. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592: A classificação por preço não funciona para produtos com preço zero

O patch do Adobe Commerce MDVA-37592 resolve o problema em que a classificação por preço não funciona corretamente para produtos com preço zero atribuído a um catálogo compartilhado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 está instalada. A ID do patch é MDVA-37592. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce em nossa arquitetura de nuvem 2.4.0-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os tipos de implantação) 2.3.6-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

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

* Adobe Commerce no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) em nossa documentação para desenvolvedores.
* Adobe Commerce em nossa arquitetura de nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) em nossa documentação de desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

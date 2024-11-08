---
title: "MDVA-44533: Desconto aplicado incorretamente ao produto filho agrupado"
description: O patch MDVA-44533 corrige o problema em que um desconto é aplicado incorretamente a um produto filho agrupado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 está instalada. A ID do patch é MDVA-44533. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 84302ed4-d850-45e4-8b5b-44495f9df820
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-44533: Desconto aplicado incorretamente ao produto filho agrupado

O patch MDVA-44533 corrige o problema em que um desconto é aplicado incorretamente a um produto filho agrupado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 está instalada. A ID do patch é MDVA-44533. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O desconto é aplicado incorretamente a um produto secundário agrupado.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples com preço de 50$.
1. Crie um produto agrupado e atribua o produto simples como a única opção para o produto agrupado.
1. Criar uma regra de preço do carrinho com:

   * Condição: se o valor total for maior que 130$
   * Ação: desconto de valor fixo de 10$ é aplicado

1. Vá para a loja e adicione o produto do pacote ao carrinho com qty = 1.
1. Acesse o carrinho e verifique se o custo total do produto do pacote é de 50$ e o desconto não se aplica.
1. Altere a quantidade para 2 e atualize o carrinho. O custo total do produto incorporado agora deve ser de 100$.

<u>Resultados esperados</u>:

O desconto não é aplicado porque o subtotal é 100\$, que é menor que 130\$ na condição de regra.

<u>Resultados reais</u>:

O desconto é aplicado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.

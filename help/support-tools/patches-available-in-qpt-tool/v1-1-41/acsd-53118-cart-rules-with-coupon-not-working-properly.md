---
title: "ACSD-53118: as regras do carrinho com cupom não estão funcionando corretamente"
description: Aplique o patch ACSD-53118 para corrigir o problema do Adobe Commerce em que a regra de preço do carrinho é aplicada usando um código de cupom enquanto o produto no carrinho tem um atributo correspondente vazio.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: a660ddb3-03fc-4460-b2a8-8e851f57e7a9
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-53118: as regras do carrinho com cupom não funcionam corretamente

O patch ACSD-53118 corrige o problema em que a regra de preço do carrinho é aplicada usando um código de cupom, enquanto o produto no carrinho tem um atributo correspondente vazio. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.41 está instalado. A ID do patch é ACSD-53118. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A regra de preço do carrinho é aplicada usando um código de cupom, enquanto o produto no carrinho tem um atributo correspondente vazio.

<u>Etapas a serem reproduzidas</u>:

1. Crie um atributo de preço e adicione-o ao conjunto de atributos. Tornar o atributo utilizável em condições de regra promocional.
1. Crie um produto e deixe o novo atributo vazio.
1. Crie uma regra de preço do carrinho com um cupom específico e a seguinte condição:

   * Se um item for ENCONTRADO no carrinho com TODAS essas condições true: Attribute1 é 0.

1. Adicione o produto criado na Etapa 2 ao carrinho.
1. Use o código do cupom para a regra do carrinho criada na Etapa 3.

<u>Resultados esperados</u>:

O desconto não é aplicado ao carrinho de compras.

<u>Resultados reais</u>:

O desconto é aplicado ao carrinho de compras.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

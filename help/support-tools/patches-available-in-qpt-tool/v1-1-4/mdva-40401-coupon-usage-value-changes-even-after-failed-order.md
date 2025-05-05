---
title: 'MDVA-40401: o valor de uso do cupom muda após uma ordem com falha'
description: O patch MDVA-40401 corrige o problema em que o valor de uso do cupom muda mesmo após um pedido com falha. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 está instalada. A ID do patch é MDVA-40401. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401: o valor de uso do cupom muda após uma ordem com falha

O patch MDVA-40401 corrige o problema em que o valor de uso do cupom muda mesmo após um pedido com falha. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 está instalada. A ID do patch é MDVA-40401. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários não podem reaplicar o cupom depois de usá-lo em uma ordem com falha.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma regra de carrinho de compras com cupons gerados automaticamente.
1. Adicione um produto ao carrinho e aplique o cupom.
1. Ir para **Check-out**.
1. Deixe o produto adicionado &quot;esgotado&quot; antes de fazer o pedido.
1. Você deve receber um erro *de estoque*.
1. Execute o cron.
1. Vá para o carrinho e remova esse produto.
1. Adicione outro produto e aplique o cupom.

<u>Resultados esperados</u>:

O código do cupom deve ser aplicado com êxito, pois o pedido anterior não foi feito.

<u>Resultados reais</u>:

Você recebe um erro *o código do cupom é inválido*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

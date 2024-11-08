---
title: "MDVA-32776: status do estoque não atualizado com o posicionamento do pedido"
description: O patch MDVA-32776 corrige o problema em que o status do estoque não é atualizado quando um pedido é feito, mas não enviado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 está instalada. A ID do patch é MDVA-32776. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776: Status do estoque não atualizado com posicionamento do pedido

O patch MDVA-32776 corrige o problema em que o status do estoque não é atualizado quando um pedido é feito, mas não enviado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 está instalada. A ID do patch é MDVA-32776. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do estoque não é atualizado quando um pedido é feito, mas não enviado.

<u>Pré-requisitos</u>:

1. O módulo de inventário está instalado.
1. Exibir Produtos Indisponíveis está definido como *Sim*.

   Para definir, vá para **Lojas** > **Configuração** > **Catálogo** > **Inventário** > **Exibir Produtos Indisponíveis** = *Sim*.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos simples com quantidade = 11 e 22.
1. Crie um produto agrupado usando os produtos simples criados na etapa um.
1. Adicione produtos agrupados ao carrinho definindo uma da quantidade de produtos como 11 e fazendo com que o outro produto simples fique indisponível.
1. Conclua a finalização e faça o pedido.

<u>Resultados esperados</u>:

Os produtos agrupados exibem `out-of-stock` rótulos quando os produtos simples associados não estão mais disponíveis.

<u>Resultados reais</u>:

1. O produto simples com qtd. = 11 mostra o produto esgotado.
1. O produto agrupado não mostra uma mensagem *indisponível* para o produto com qtd. = 11. No entanto, adicionar este produto ao carrinho resulta em um erro *indisponível*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

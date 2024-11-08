---
title: "MDVA-40488: produtos configuráveis com produtos secundários indisponíveis não mostrados na faixa de preço correta"
description: O patch MDVA-40488 resolve o problema em que os produtos configuráveis com produtos secundários esgotados não são mostrados em sua faixa de preço correta. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-40488. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488: produtos configuráveis com produtos secundários indisponíveis não mostrados na faixa de preço correta

O patch MDVA-40488 resolve o problema em que os produtos configuráveis com produtos secundários esgotados não são mostrados em sua faixa de preço correta. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-40488. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos configuráveis com produtos secundários indisponíveis não são mostrados em sua faixa de preço correta.

<u>Pré-requisitos</u>:

Acesse Administrador do Commerce > **lojas** > **configuração** > **catálogo** > **Inventário** > **opções de ações** e defina a configuração **Exibir Produtos sem Estoque** como *Sim*.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com dois produtos associados. Por exemplo: produtos simples Vermelho e Marrom.
1. Defina o estoque do produto simples como Vermelho, o Status do Estoque como *No Estoque* e o status Habilitar Produto como *Não*.
1. Defina o inventário do produto simples Brown e o status Habilitar Produto como *Sim*.
1. Verifique se o Status do Estoque do produto configurável é *No Estoque*.
1. Altere o inventário do produto simples Brown para 0 e defina o Status do Estoque como *Sem Estoque*.
1. Neste ponto, o status configurável do estoque do produto ainda é *No Stock*.
1. Executar reindexação.
1. Verifique o `min_price` e o `max_price` do produto configurável na tabela de banco de dados `catalog_product_index_price` - os dois valores são definidos como 0.
1. Mas se definirmos o Status do Estoque do produto configurável como *Sem estoque* e reindexarmos, poderemos ver valores diferentes de zero `min_price` e `max_price` do produto configurável.

<u>Resultados esperados</u>:

Se todos os produtos derivados estiverem *Sem Estoque* e o próprio produto configurável também estiver *Sem Estoque*, o preço será calculado usando todos os produtos derivados.

<u>Resultados reais</u>:

Os valores `min_price` e `max_price` do produto configurável na tabela de banco de dados `catalog_product_index_price` são definidos como 0 quando o status do estoque configurável é *No estoque*, mas se for *Fora do Estoque* eles se tornam valores diferentes de zero.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.

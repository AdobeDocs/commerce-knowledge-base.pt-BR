---
title: "MDVA-28651: B2B - aspas lentas para carregar"
description: O patch MDVA-28651 resolve o problema em que vários problemas de desempenho ocorrem com cotas de carregamento. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 está instalada. Observe que o problema foi agendado para ser corrigido no Adobe Commerce versão 2.4.2.
exl-id: 2d0bfbba-cdf3-4f9e-a900-ce42909fac8e
feature: B2B, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-28651: B2B - carregamento lento

O patch MDVA-28651 resolve o problema em que vários problemas de desempenho ocorrem com cotas de carregamento. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 está instalada. Observe que o problema foi agendado para ser corrigido no Adobe Commerce versão 2.4.2.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.3.4.
* O patch também é compatível com as seguintes versões do Adobe Commerce: Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.0-2.3.5-p1, 2.4.0 e 2.4.1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Problemas de desempenho na página da lista de cotações do cliente:

* carregamento duplo da lista de cotações: primeiro com a página inteira, segundo por solicitação de Ajax.
* um loop de carregar cada uma das aspas do plug-in.
* carregamento duplo dos itens de cotação quando a cotação foi convertida no instantâneo.

<u>Etapas a serem reproduzidas</u>

1. Mais de 40 cotações atribuídas a um cliente.
1. Faça logon e navegue pela página **Minhas Cotações**.

<u>Resultado real</u>

O tempo de resposta para carregar totalmente o conteúdo da página **Minhas Cotações** (carregamento da página + dados mostrados na grade) é ~ 45 segundos.

<u>Resultado esperado</u>

O tempo de resposta para carregar totalmente o conteúdo da página **Minhas Cotações** deve ser inferior a 45 segundos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

---
title: "Correção MDVA-33482: erro de cálculo de imposto no aviso de crédito"
description: O patch MDVA-33482 resolve o problema em que o imposto é calculado incorretamente em avisos de crédito.
exl-id: 80740e6f-2b6c-4770-9a1a-58ba68a1b28f
feature: Orders, Returns, Taxes
role: Admin
source-git-commit: 0ffa6d63f7046048f7e8f0e9fab1ee1869c98e93
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Correção MDVA-33482: erro de cálculo de imposto no aviso de crédito

O patch MDVA-33482 resolve o problema em que o imposto é calculado incorretamente em avisos de crédito quando não há Taxa de Ajuste ou Restituição de Ajuste aplicada.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.5 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Configurar **Impostos**.
1. Crie um pedido usando dois produtos no back-end usando qualquer método de pagamento online (Exemplo: [!DNL PayPal Payment Pro]). Verifique se os impostos são aplicados a todos os produtos.
1. Criar duas faturas para o pedido.
1. Crie um aviso de crédito contra uma das NFFs. Observe que a solução não será aplicável se você planejar aplicar uma Taxa de Ajuste ou Restituição de Ajuste.
1. Verifique os totais do aviso de crédito.

<u>Resultados esperados</u>:

Somente uma quantia de imposto parcialmente faturada está no aviso de crédito, conforme esperado.

<u>Resultados reais</u>:

O valor total do imposto é exibido no aviso de crédito.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

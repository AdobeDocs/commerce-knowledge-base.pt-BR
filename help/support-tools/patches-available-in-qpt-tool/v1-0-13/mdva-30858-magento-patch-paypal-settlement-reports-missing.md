---
title: "MDVA-30858: Relatórios de liquidação do PayPal ausentes"
description: "O patch MDVA-30858 corrige a falta de Relatórios de liquidação do PayPal ao ter várias contas do PayPal. Os relatórios devem estar disponíveis na barra lateral Admin &gt; **Reports** &gt; Sales &gt; **PayPal Settlement**. Em vez disso, a mensagem: *Não foi possível encontrar nenhum registro.* é exibido. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2."
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858: Relatórios de Liquidação do PayPal ausentes

O patch MDVA-30858 corrige a falta de Relatórios de liquidação do PayPal ao ter várias contas do PayPal. Os relatórios devem estar disponíveis na barra lateral Admin > **Relatórios** > Vendas > **Acordo PayPal**. Em vez disso, a mensagem: *Não foi possível encontrar nenhum registro.* exibições. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.4

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige o problema em que nenhum registro era encontrado em **Relatórios** > Vendas > **Liquidação do PayPal** ao ter várias contas do PayPal.

<u>Etapas a serem reproduzidas</u>:

1. Configurar Relatórios de liquidação do PayPal.
1. Vá para Admin, para **Relatórios** > Vendas > **Acordo PayPal**.
1. Para obter as atualizações mais recentes, clique em **Buscar atualizações** no canto superior direito.

<u>Resultados esperados</u>:

Os relatórios devem aparecer.

<u>Resultados reais</u>:

Nada é exibido na grade, embora os relatórios estejam disponíveis.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

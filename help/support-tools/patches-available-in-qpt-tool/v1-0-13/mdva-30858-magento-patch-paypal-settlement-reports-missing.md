---
title: "MDVA-30858: Relatórios de liquidação do PayPal ausentes"
description: "O patch MDVA-30858 corrige a falta de Relatórios de liquidação do PayPal ao ter várias contas do PayPal. Os relatórios devem estar disponíveis na barra lateral do Admin &gt; **Relatórios** &gt; Vendas &gt; **Acordo com o PayPal**. Em vez disso, a mensagem: *Não foi possível encontrar nenhum registro.* é exibido. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2."
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858: Relatórios de Liquidação do PayPal ausentes

O patch MDVA-30858 corrige a falta de Relatórios de liquidação do PayPal ao ter várias contas do PayPal. Os relatórios devem estar disponíveis na barra lateral Admin > **Relatórios** > Vendas > **Liquidação do PayPal**. Em vez disso, a mensagem: *Não foi possível encontrar nenhum registro.* é exibido. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.13 está instalado. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.4

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige o problema em que nenhum registro foi encontrado no **Relatórios** > Vendas > **Liquidação do PayPal** ao ter várias contas do PayPal.

<u>Etapas a serem reproduzidas</u>:

1. Configurar Relatórios de liquidação do PayPal.
1. Acesse Administrador para **Relatórios** > Vendas > **Liquidação do PayPal**.
1. Para obter as atualizações mais recentes, clique em **Buscar atualizações** no canto superior direito.

<u>Resultados esperados</u>:

Os relatórios devem aparecer.

<u>Resultados reais</u>:

Nada é exibido na grade, embora os relatórios estejam disponíveis.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

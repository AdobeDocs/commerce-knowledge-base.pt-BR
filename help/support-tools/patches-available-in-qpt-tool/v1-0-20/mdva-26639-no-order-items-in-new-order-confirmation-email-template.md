---
title: "MDVA-26639: nenhum item de pedido no novo modelo de email de confirmação de pedido"
description: O patch MDVA-26639 corrige o problema quando um novo pedido é criado, os itens do pedido estão ausentes em um modelo de email de confirmação.
exl-id: 5d9716ab-6e57-47b0-8b38-ca98a98101e8
feature: Communications, Marketing Tools, Native Luma Frontend Development, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# MDVA-26639: nenhum item de pedido no modelo de email de confirmação de novo pedido

O patch MDVA-26639 corrige o problema quando um novo pedido é criado, os itens do pedido estão ausentes em um modelo de email de confirmação.

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.20 está instalado. A ID do patch é MDVA-26639. Observe que o problema foi corrigido no Adobe Commerce 2.3.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.3-p1

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Ir para **Lojas** > **Configuração** > **Vendas** > **Emails de vendas** > **Confirmação de novo pedido** e selecione **Modelo: Nova Ordem de Retirada**.
1. Ir para **Vendas** > **Ordem: Selecione uma ordem**, em seguida, vá para **Informações** e selecione **Enviar e-mail**.

<u>Resultados esperados</u>:

Os itens do pedido são exibidos no e-mail de pedido do cliente, conforme esperado.

<u>Resultados reais</u>:

Os itens do pedido estão ausentes no email de pedido do cliente. O mesmo se aplica se você criar um novo modelo e selecionar um modelo Nova ordem ou Nova ordem (Luma).

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.

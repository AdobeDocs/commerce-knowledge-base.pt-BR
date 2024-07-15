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

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-26639. Observe que o problema foi corrigido no Adobe Commerce 2.3.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.3.3-p1

**Compatível com as versões do Adobe Commerce:** Adobe Commerce local e Adobe Commerce na infraestrutura em nuvem 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Acesse **Lojas** > **Configuração** > **Vendas** > **Emails de Vendas** > **Confirmação de Novo Pedido** e selecione **Modelo: Novo Pedido de Seleção**.
1. Ir para **Vendas** > **Pedido: selecione um pedido**, vá para **Informações** e selecione **Enviar Email**.

<u>Resultados esperados</u>:

Os itens do pedido são exibidos no e-mail de pedido do cliente, conforme esperado.

<u>Resultados reais</u>:

Os itens do pedido estão ausentes no email de pedido do cliente. O mesmo se aplica se você criar um novo modelo e selecionar um modelo Nova ordem ou Nova ordem (Luma).

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

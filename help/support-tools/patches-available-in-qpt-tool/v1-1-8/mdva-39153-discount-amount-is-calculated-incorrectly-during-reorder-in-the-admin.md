---
title: "MDVA-39153: o valor do desconto é calculado incorretamente durante a reorganização no Administrador"
description: O patch MDVA-39153 corrige o problema em que o valor do desconto é calculado incorretamente durante o novo pedido no Administrador. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 está instalada. A ID do patch é MDVA-39153. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: d4d11bea-a528-4eb5-8a57-8a7330975e4a
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-39153: o valor do desconto é calculado incorretamente durante o reordenamento no Administrador

O patch MDVA-39153 corrige o problema em que o valor do desconto é calculado incorretamente durante o novo pedido no Administrador. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 está instalada. A ID do patch é MDVA-39153. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O valor do desconto é calculado incorretamente durante o reordenamento no Administrador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Admin** > **Lojas** > **Configuração** > **Vendas** > **Impostos**.
1. Ativar o imposto para entrega exibindo o imposto no Carrinho de Compras.
1. Habilite e configure o método de envio com taxa de tabela ($15).
1. Crie uma regra de imposto para alíquota de imposto embutida (para CA).
1. Crie uma regra de preço do carrinho com um desconto fixo de US$ 5 aplicado ao carrinho inteiro e à quantia de envio.
1. Adicione um produto com um preço de US$ 12 ao carrinho e vá para a página Carrinho de compras.
1. Aplique o desconto ao carrinho.
1. Defina o método de envio na seção &quot;estimativas&quot; como &quot;Taxa única&quot;.
1. Prossiga com o check-out até as etapas de revisão (não faça o pedido).
1. Vá para a página inicial e volte ao Carrinho de Compras.
1. Altere o método de envio na seção &quot;estimativas&quot; para &quot;Taxa de tabela&quot;.

<u>Resultados esperados</u>:

O desconto permanece o mesmo - US$ 5.

<u>Resultados reais</u>:

O desconto é de US$ 6,31.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

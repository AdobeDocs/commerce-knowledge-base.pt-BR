---
title: "MDVA-31007: exibição de atributos de endereço personalizados"
description: O patch MDVA-31007 resolve o problema em que os atributos de endereço personalizados não são exibidos corretamente na página de detalhes do pedido na área Minha conta e no back-end (no local **Vendas &gt; Pedidos**). Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007: exibição de atributos de endereço personalizados

O patch MDVA-31007 resolve o problema em que os atributos de endereço personalizados não são exibidos corretamente na página de detalhes do pedido na área Minha Conta e no back-end (no local **Vendas > Pedidos**). Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no back-end do administrador.
1. Navegue até **Lojas** > **Atributos** > **Endereços de Clientes**.
1. Crie dois atributos:

   * Definir tipo de entrada: *Suspenso*.
   * Definir tipo de entrada: *Texto*.

1. Navegue até **Lojas** > **Configurações** > **Cliente** > **Configurações de Cliente**.
1. Selecione *Escopo* como exibição de **Repositório Padrão**.
1. Expanda a seção **Modelo de Endereço**. Atualize *Texto*, *Texto Uma Linha* e *HTML* para incluir os dois atributos personalizados acima:

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. Abra a Storefront.
1. Criar e fazer logon com um usuário.
1. Vá para **Minha Conta** > **Catálogo de endereços** e adicione um novo endereço (preencha os dois atributos personalizados).
1. Adicione um produto ao carrinho e faça um pedido.
1. Na página de sucesso do pedido, clique no link **Número do pedido**.
1. Na página de detalhes do pedido, observe a seção **Informações do pedido**.
1. Vá para **Back-end** > **Vendas** > **Pedidos**, clique no pedido acima e observe a seção **Informações de endereço**.

<u>Resultados esperados</u>:

Tanto no front-end quanto no back-end, o endereço de faturamento e entrega são exibidos conforme esperado.

<u>Resultados reais</u>:

O endereço de cobrança não é exibido corretamente no front-end e no back-end. A opção selecionada do atributo suspenso está ausente e o valor do atributo de entrada contém o código do atributo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

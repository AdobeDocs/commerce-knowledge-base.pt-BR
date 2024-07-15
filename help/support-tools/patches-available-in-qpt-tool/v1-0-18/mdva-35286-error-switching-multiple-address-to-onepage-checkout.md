---
title: "MDVA-35286: erro ao alternar Vários Endereços para Check-out de Uma Página"
description: O patch MDVA-35286 corrige o problema em que há um erro se um cliente tiver pacotes de produtos no carrinho e alternar do checkout de Vários endereços para o checkout de Uma página. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalada. A ID do patch é MDVA-35286. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 40c98735-6054-4b25-9882-e274424b203f
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-35286: erro ao alternar o check-out de Vários Endereços para Uma Página

O patch MDVA-35286 corrige o problema em que há um erro se um cliente tiver pacotes de produtos no carrinho e alternar do checkout de Vários endereços para o checkout de Uma página. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalada. A ID do patch é MDVA-35286. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.0-2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um erro é exibido se houver um produto incluído no carrinho e o usuário tentar usar o Check-out de uma página após abandonar o Check-out de várias remessas.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon na conta do cliente e adicione mais de um pacote de produtos ao carrinho.
1. Clique no link para exibir e editar o carrinho.
1. Clique no link **Fazer Check-out com Vários Endereços**.
1. Selecione endereços diferentes para os produtos adicionados ao carrinho.
1. Clique em **Voltar ao carrinho de compras**.
1. No carrinho, clique em **Prosseguir para a finalização da compra**.

<u>Resultados esperados</u>:

Você será redirecionado para a página Finalização da compra.

<u>Resultados reais</u>:

A mensagem de erro é exibida: *Houve um erro ao processar sua solicitação*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

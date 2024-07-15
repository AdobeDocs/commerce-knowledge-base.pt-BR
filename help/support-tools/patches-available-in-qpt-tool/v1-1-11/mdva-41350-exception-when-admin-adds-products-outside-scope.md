---
title: "MDVA-41350: exceção quando o administrador adiciona produtos fora de seu acesso"
description: O patch MDVA-41350 corrige o problema em que um erro de exceção é lançado em vez de uma notificação de acesso limitado quando um usuário administrador adiciona um produto no pedido pelo SKU, que está fora do acesso dele. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 está instalada. A ID do patch é MDVA-41350. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 3a96d029-5350-4dd6-aad3-2f2cdd5e65ac
feature: Admin Workspace, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-41350: exceção quando o administrador adiciona produtos fora de seu acesso

O patch MDVA-41350 corrige o problema em que um erro de exceção é lançado em vez de uma notificação de acesso limitado quando um usuário administrador adiciona um produto no pedido pelo SKU, que está fora do acesso dele. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 está instalada. A ID do patch é MDVA-41350. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando um usuário administrador com acesso restrito adiciona um produto pelo SKU fora de seu acesso na ordem, ocorre uma exceção em vez de uma mensagem notificando o usuário sobre seu acesso limitado.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no administrador como um usuário com acesso somente a um site específico.
1. Vá para **Vendas** > **Pedidos** e clique em **Criar novo pedido**.
1. Selecione um cliente e uma visualização de loja.
1. Clique em **Adicionar produtos por SKU**.
1. Procure por um SKU que não esteja atribuído a nenhum site ou não esteja atribuído ao site para o qual você tem acesso.
1. Clique em **Adicionar à Ordem**.

<u>Resultados esperados</u>:

Uma mensagem de erro apropriada é exibida.

<u>Resultados reais</u>:

Ocorre uma exceção.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

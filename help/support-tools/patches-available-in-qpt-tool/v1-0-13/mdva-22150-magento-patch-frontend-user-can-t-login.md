---
title: "Patch MDVA-22150 do Adobe Commerce: o usuário de front-end não consegue fazer logon"
description: O patch MDVA-22150 resolve o problema quando um usuário de front-end não consegue fazer logon após uma compra anulada usando um cupom. Isso ocorre quando um usuário de front-end usa um código de cupom em um produto que foi desativado antes de concluir a compra. O resultado é que o usuário de front-end não pode mais fazer logon e recebe um erro 503. Outro efeito desse problema é que a capacidade de gerenciar os carrinhos de compras dos clientes no Administrador para de funcionar.
exl-id: 8aabe7b2-4b8a-4339-914e-7131006907b3
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Correção do MDVA-22150 Adobe Commerce: o usuário de front-end não consegue fazer logon

O patch MDVA-22150 resolve o problema quando um usuário de front-end não consegue fazer logon após uma compra anulada usando um cupom. Isso ocorre quando um usuário de front-end usa um código de cupom em um produto que foi desativado antes de concluir a compra. O resultado é que o usuário de front-end não pode mais fazer logon e recebe um erro 503. Outro efeito desse problema é que a capacidade de gerenciar os carrinhos de compras dos clientes no Administrador para de funcionar.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.3.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce 2.3.1 - 2.3.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas:</u>

1. Faça logon no Admin e crie um produto configurável.
1. Vá para **Regras do carrinho** e crie um código de cupom com algum desconto.
1. Crie uma conta de cliente no front-end.
1. Adicione o produto ao carrinho, siga o processo de finalização e insira o cupom.
1. Depois de inserir o cupom, não envie o pedido, mas cancele o pedido e faça logoff.
1. Retorne ao Administrador e desative todo o produto configurável.

<u>Resultados esperados:</u>

O produto não é exibido no carrinho na Loja nem é exibido com a mensagem de erro apropriada informando que o produto foi desativado, conforme esperado.

<u>Resultados reais:</u>

* Ao tentar fazer logon novamente na interface do, você ficará preso em um loop infinito (que eventualmente mostrará uma exceção após um longo período).
* A capacidade de gerenciar os carrinhos de compras dos clientes no Admin para de funcionar.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

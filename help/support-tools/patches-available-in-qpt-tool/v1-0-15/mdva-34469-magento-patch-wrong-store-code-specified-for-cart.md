---
title: 'MDVA-34469: código de armazenamento incorreto especificado para o carrinho'
description: '"O patch MDVA-34469 resolve o problema em que os usuários recebem a mensagem de erro: *Código de armazenamento incorreto especificado para o carrinho* ao adicionar um produto ao carrinho após alternar as exibições da loja. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 está instalada. A ID do patch é MDVA-34469. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.'''
exl-id: 35d4f120-7fcf-4996-8b23-aca99cfc18ac
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-34469: Código de armazenamento incorreto especificado para o carrinho

O patch MDVA-34469 resolve o problema em que os usuários recebem a mensagem de erro: *Código de armazenamento incorreto especificado para o carrinho* ao adicionar um produto ao carrinho após alternar exibições da loja. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 está instalada. A ID do patch é MDVA-34469. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário vê um erro de consulta de carrinho, *&quot;Código de armazenamento incorreto especificado para o carrinho&quot;*, ao tentar alternar exibições de armazenamento.

<u>Pré-requisitos</u>:

* Adobe Commerce 2.4.0
* Um único site com uma única loja e duas visualizações de loja está configurado.
* Uma conta de cliente é criada.

<u>Etapas a serem reproduzidas</u>:

1. O back-end do Adobe Commerce está configurado para ter duas exibições de loja (com códigos de loja: padrão, segundo).
1. O usuário cria um carrinho de compras usando o código de loja padrão.
1. O usuário tenta recuperar esse carrinho usando o segundo código de armazenamento no cabeçalho da solicitação `Store`.

<u>Resultados esperados</u>:

O carrinho é exibido porque alternar o armazenamento (enviando o novo código no cabeçalho de solicitação `Store`) associa o carrinho ao armazenamento solicitado.

<u>Resultados reais</u>:

O query de carrinho retorna um erro e o carrinho não é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

---
title: "MDVA-37874: desconto fixo não aplicado a todo o carrinho"
description: O patch MDVA-37874 corrige o problema quando o **valor de desconto fixo** para o carrinho inteiro é aplicado incorretamente a um produto de pacote que contém mais de uma opção. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24 está instalada. A ID do patch é MDVA-37874. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.
exl-id: a1c414f0-b654-4b18-b502-47351513ddfa
feature: Orders, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-37874: desconto fixo não aplicado a todo o carrinho

O patch MDVA-37874 corrige o problema quando a variável **valor do desconto fixo** para o carrinho inteiro é aplicado incorretamente a um produto de pacote que contém mais de uma opção. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.24 está instalado. A ID do patch é MDVA-37874. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.4.2
* O patch também é compatível com o Adobe Commerce no local e o Adobe Commerce na infraestrutura de nuvem 2.3.6-2.3.7 e 2.4.1-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema


<u>Etapas a serem reproduzidas</u>:

1. Criar uma regra de carrinho com um **valor do desconto fixo** para o carrinho inteiro.
1. Adicione um produto do pacote ao carrinho (o produto do pacote deve conter várias opções selecionadas).
1. Acesse a página do carrinho e marque o desconto.


<u>Resultados esperados</u>:

O valor fixo do desconto é aplicado a todo o carrinho, conforme esperado.

<u>Resultados reais</u>:

O valor fixo do desconto é aplicado somente a parte do carrinho.


## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.

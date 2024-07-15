---
title: "Patch MDVA-33976: pacote fora de estoque após a opção removida"
description: O patch MDVA-33976 corrige o problema em que um produto de pacote é mostrado como Fora de estoque depois que uma de suas opções é removida no Admin. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) é instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 2e2bc05b-ad31-4e87-b33e-3526f6a42478
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# Correção MDVA-33976: pacote Fora de Estoque após a opção removida

O patch MDVA-33976 corrige o problema em que um produto de pacote é mostrado como Fora de estoque depois que uma de suas opções é removida no Admin. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) é instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.3

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem e Adobe Commerce no local 2.3.0-2.3.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Abra um produto incluído no Administrador do Commerce.
1. Remova uma das opções de produto do pacote.
1. Salve as alterações.
1. Abra o produto na loja.

<u>Resultado esperado</u>:

O status do estoque de produtos do pacote é atualizado de acordo com o status do estoque de produtos filho.

<u>Resultado real</u>:

O produto do pacote é exibido como Fora de estoque, independentemente do status do produto filho.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

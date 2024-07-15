---
title: "MDVA-37082: índice parcial incorreto do status do estoque de produtos agrupados"
description: O patch de Magento MDVA-37082 corrige o problema quando o índice parcial do status do estoque de produtos agrupados está incorreto para estoques personalizados. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 está instalada. A ID do patch é MDVA-37082. Observe que o problema está programado para ser corrigido na Magento 2.4.4.
exl-id: 1c0abc99-bd24-4848-87a3-227a63655cb7
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-37082: índice parcial incorreto do status do estoque de produtos agrupados

O patch de Magento MDVA-37082 corrige o problema quando o índice parcial do status do estoque de produtos agrupados está incorreto para estoques personalizados. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 está instalada. A ID do patch é MDVA-37082. Observe que o problema está programado para ser corrigido na Magento 2.4.4.


## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
Adobe Commerce na infraestrutura em nuvem 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**
Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.0-2.4.2-p1
>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A indexação incremental de produtos secundários de produtos agrupados pode fazer com que outros produtos agrupados incorretos sejam indexados incorretamente quando os secundários são compartilhados.

<u>Etapas a serem reproduzidas</u>:

* Criar um novo estoque e fonte para o site principal.
* Crie 3 produtos simples com quantidade 10,15 e 0.
* Crie 2 produtos agrupados e atribua o primeiro produto simples com qtde 10 para um e outros 2 produtos simples para o outro.
* Confirme se ambos os produtos agrupados podem ser acessados no front-end, no estoque.
* Atribua o produto simples com quantidade 0 aos Produtos de venda adicional do primeiro produto agrupado.
* Limpe o cache de página inteira e verifique o 2º produto agrupado do front-end.
* Execute uma reindexação completa.
* Verifique o 2º produto agrupado no front-end.
* Salve o primeiro produto agrupado.
* Limpe o cache de página inteira e verifique o 2º produto agrupado do front-end.

<u>Resultados esperados</u>:

O produto agrupado não está esgotado depois de salvar outro produto agrupado com venda adicional. O problema é resolvido após uma reindexação completa.

<u>Resultados reais</u>:

O 2º Produto Agrupado fica indisponível quando você salva o 1º Produto Agrupado.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links para a documentação do desenvolvedor, dependendo do método de implantação do Adobe Commerce:

* Adobe Commerce local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) em nossa documentação de desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se o patch está disponível para o problema de Magento usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

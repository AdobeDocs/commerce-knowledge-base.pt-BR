---
title: "MDVA-37913: os links de download do produto desaparecem após a atualização dos atributos de extensão por meio da API"
description: O patch de MDVA-37913 para o resolve o problema em que os links de produtos baixáveis desaparecem após a atualização dos atributos de extensão por meio da API. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 está instalada. A ID do patch é MDVA-37913. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: e4b2cf59-5c35-4a28-a63e-15cd7d0d5a5d
feature: REST, Attributes, Extensions, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-37913: os links de download do produto desaparecem após a atualização dos atributos de extensão por meio da API

O patch de MDVA-37913 para o resolve o problema em que os links de produtos baixáveis desaparecem após a atualização dos atributos de extensão por meio da API. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.24 está instalado. A ID do patch é MDVA-37913. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.


## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
Adobe Commerce na infraestrutura em nuvem 2.3.6

**Compatível com as versões do Adobe Commerce:**
Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.0 - 2.4.0-p1
>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.


## Problema

Os links de produto baixáveis desaparecem após atualizar atributos de extensão por meio da API.

<u>Pré-requisitos</u>: produto baixável com links de download.

<u>Etapas a serem reproduzidas</u>:

1. Atualize os atributos da extensão usando a solicitação como esta:

```JSON
{
    "product": {
        "extension_attributes": {
            "stock_item": {
                "is_in_stock": true,
                "qty": 100
            }
        }
    }
}
```

<u>Resultados esperados</u>:<br>
O produto é atualizado, todos os links de download não são removidos.

<u>Resultados reais</u>:<br>
Produto atualizado, mas todos os links de download foram removidos.


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Leitura relacionada

Para saber mais sobre a Ferramenta de correções de qualidade em nossa base de conhecimento de suporte, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção em nossa base de conhecimento de suporte.

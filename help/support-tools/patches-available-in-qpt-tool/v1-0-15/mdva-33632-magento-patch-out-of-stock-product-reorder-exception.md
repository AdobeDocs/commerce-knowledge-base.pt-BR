---
title: "Patch MDVA-33632: exceção de reordenação de produto esgotado"
description: O patch MDVA-33632 resolve o problema em que uma exceção é lançada ao tentar reordenar um produto indisponível.
exl-id: 4a970db4-a64c-49b5-8c5f-8b9c5cdd946f
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Correção MDVA-33632: exceção de reordenação de produto indisponível

O patch MDVA-33632 resolve o problema em que uma exceção é lançada ao tentar reordenar um produto indisponível.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.6

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem e Adobe Commerce no local 2.3.0 - 2.3.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com uma opção (Exemplo: **cor** = *vermelho*) e defina **qty** = *1*.
1. Crie um cliente e faça um pedido com este produto, que nesse momento se tornará **qty** = *0*.
1. Acesse Admin e tente reordenar o pedido anterior.

<u>Resultados esperados</u>:

O cliente obtém o &quot;*Este produto está esgotado.* mensagem de produto indisponível, conforme esperado.

<u>Resultados reais</u>:

O cliente obtém o &quot;*Este produto está esgotado.*&quot; mensagem, e `var/log/exception.log` contém uma exceção semelhante:

```php
[2020-12-09 00:17:36] report.CRITICAL: This product is out of stock. {"exception":"[object] (Magento\\Framework\\Exception\\LocalizedException(code: 0): This product is out of stock. at /vendor/magento/module-quote/Model/Quote.php:1711)"} []
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis em QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

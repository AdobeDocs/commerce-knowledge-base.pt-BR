---
title: 'MDVA-34886: nenhum resultado de pesquisa quando o atributo "weight" for usado'
description: O patch MDVA-34886 resolve o problema em que a pesquisa retorna resultados quando o atributo weight é configurado como pesquisável. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: e6f33772-0167-4a54-9d62-0ab89edb5d1d
feature: Attributes, Cache, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-34886: nenhum resultado de pesquisa quando o atributo &quot;weight&quot; é usado

O patch MDVA-34886 resolve o problema em que a pesquisa retorna resultados quando o atributo weight é configurado como pesquisável. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.2 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A pesquisa retorna resultados quando o atributo de peso é configurado como pesquisável.

<u>Etapas a serem reproduzidas</u>:

1. Configurar o Elasticsearch.
1. Navegue até **Admin** > **Lojas** > **Atributos** > **Produto**. Edite o atributo **Weight** e defina seu atributo **Searchable** = *Yes*.
1. Salve o atributo e limpe o cache de configuração.
1. No front-end, pesquise por um valor de texto (Exemplo: *bag*).
1. Observe que a pesquisa não retorna nenhum resultado.
1. O log de exceções conterá uma mensagem de erro como:

```php
{"type":"number_format_exception","reason":"For input string: \"bag\""}
```

<u>Resultados esperados</u>:

A Pesquisa retorna resultados mesmo quando o atributo de peso é configurado como pesquisável, conforme esperado.

<u>Resultados reais</u>:

A Pesquisa não retorna resultados quando o atributo de peso é configurado como pesquisável.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

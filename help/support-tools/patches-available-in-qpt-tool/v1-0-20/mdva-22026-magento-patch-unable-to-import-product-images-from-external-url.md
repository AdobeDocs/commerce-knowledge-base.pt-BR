---
title: "MDVA-22026: não é possível importar imagens de produtos do URL externo"
description: O patch do MDVA-22026 corrige o problema de não ser possível importar imagens de produtos de um URL externo.
exl-id: 29043c6c-daf2-4925-85bf-49eeeee3742c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# MDVA-22026: Não é possível importar imagens de produtos do URL externo

O patch do MDVA-22026 corrige o problema de não ser possível importar imagens de produtos de um URL externo.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-22026. Observe que o problema foi corrigido no Adobe Commerce versão 2.3.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.3.2-p2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local e Adobe Commerce na infraestrutura de nuvem 2.3.2-2.3.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Em Administração, vá para **Sistema** > **Importar**.
1. Definir **Tipo De Entidade** = *Produtos*.
1. Definir **Comportamento De Importação** = *Adicionar/Atualizar*.
1. Definir **Contagem de Erros Permitidos** = *10000*.
1. Selecione o arquivo a ser importado.
1. Clique no botão **Verificar Dados** (que deve validar o arquivo).
1. Clique no botão **Importar**.

<u>Resultados esperados</u>:

Importação bem-sucedida de produtos de arquivos CSV, incluindo imagens de URLs externos, conforme esperado.

<u>Resultados reais</u>:

Importação malsucedida de produtos de arquivos CSV, incluindo imagens de URLs externos, e receber um erro semelhante:

```php
1. Imported resource (image) could not be downloaded from external resource due to timeout or access permissions in row(s): 4, 5, 8, 9, 16, 18, 20, 21, 22, 23, 26, 27, 28, 52, 53, 55, 58, 63, 70, 71, 77, 78, 83, 84, 91
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html).
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique o problema do Adobe Commerce com a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

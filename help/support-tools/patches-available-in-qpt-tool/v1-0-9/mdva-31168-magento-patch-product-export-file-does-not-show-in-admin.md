---
title: "Patch MDVA-31168: o arquivo de exportação do produto não é exibido no Admin"
description: O patch MDVA-31168 resolve o problema em que o arquivo CSV de exportação do produto não aparece na lista de arquivos CSV exportáveis. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.2.
exl-id: 780a926b-2aea-47c2-8f95-907cc779bfa4
feature: Admin Workspace, Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Patch MDVA-31168: o arquivo de exportação do produto não é exibido no Admin

O patch MDVA-31168 resolve o problema em que o arquivo CSV de exportação do produto não aparece na lista de arquivos CSV exportáveis. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce no local 2.3.5-p2.

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisitos</u>:

Instale o Adobe Commerce com dados de amostra.

<u>Etapas a serem reproduzidas:</u>

1. Crie um produto baixável e atribua-o à categoria **Bags**.
1. Iniciar uma exportação para todos os produtos.
1. Execute o seguinte comando da CLI:    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u>Resultados esperados:</u>

O arquivo CSV de exportação do produto com todos os produtos é exibido na lista de arquivos em Administração, conforme esperado.

<u>Resultados reais:</u>

O arquivo CSV de exportação do produto com todos os produtos não é exibido na lista em Administração, embora o arquivo somente com cabeçalhos seja gerado na pasta `/var` no servidor.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

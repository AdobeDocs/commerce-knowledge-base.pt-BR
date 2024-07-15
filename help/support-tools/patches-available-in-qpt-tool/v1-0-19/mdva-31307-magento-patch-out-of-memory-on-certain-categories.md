---
title: 'MDVA-31307: memória insuficiente em determinadas categorias'
description: O patch MDVA-31307 corrige o problema em que "Magento\_Csp/Model/BlockCache" consome muita memória e gera enormes strings em cache, o que causa problemas para determinadas páginas com muitos scripts e estilos dinamicamente na lista de permissões. O patch fornecido otimiza esse processo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-31307. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307: Memória insuficiente em determinadas categorias

O patch MDVA-31307 corrige o problema em que o `Magento\_Csp/Model/BlockCache` consome muita memória e gera enormes cadeias de caracteres em cache, o que causa problemas para determinadas páginas com muitos scripts e estilos dinamicamente na lista de permissões. O patch fornecido otimiza esse processo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-31307. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:** Adobe Commerce local e Adobe Commerce na infraestrutura em nuvem 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige o problema em que há *memória insuficiente* erros em determinadas categorias devido a problemas com a lista de permissões de CSP dinâmica para blocos em cache.

<u>Etapas a serem reproduzidas:</u>

1. Gerar pequenas correções de perfil (`bin/magento setup:performance:generate-fixtures`).
1. Abra todas as páginas de categoria em guias diferentes.

<u>Resultado real:</u>

*[data e hora] Erro fatal do PHP: tamanho de memória permitido de 1073741824 bytes esgotado (tentativa de alocar 90112 bytes) em Desconhecido na linha 0
[data e hora] Erro fatal do PHP: tamanho de memória permitido de 1073741824 bytes esgotado (tentativa de alocar 33554440 bytes) em /app/`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php na linha 31*

<u>Resultado esperado:</u>

Todas as páginas foram abertas corretamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

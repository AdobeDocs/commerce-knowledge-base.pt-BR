---
title: 'MDVA-28993: pesquisa parcial Elasticsearch, "mínimo deve corresponder" e correção para "pesquisas com hífen" problema'
description: O patch MDVA-28993 implementa a funcionalidade "Mínimo deve corresponder" e a pesquisa parcial do mecanismo de Elasticsearch, e resolve problemas com hifens em consultas de pesquisa. O patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 está instalada.
exl-id: 2af0f950-284b-42f2-9660-8aafce4b04d7
feature: Search, Services
role: Admin
source-git-commit: 6f4d6382cbdb7bedddcc3f264fbf6ef997729323
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-28993: pesquisa parcial de Elasticsearch, &quot;mínimo deve corresponder&quot; e correção para &quot;pesquisas com hífen&quot; problema

O patch MDVA-28993 implementa a funcionalidade &quot;Mínimo deve corresponder&quot; e a pesquisa parcial do mecanismo de Elasticsearch, e resolve problemas com hifens em consultas de pesquisa. O patch estará disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O v.1.0.6 está instalado.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.4

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local/Adobe Commerce na infraestrutura em nuvem 2.3.4-2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.


## Problema

Ao usar o Elasticsearch 6 para pesquisar SKU que contém um hífen (-), a pesquisa retorna muitos resultados.

<u>Etapas a serem reproduzidas:</u>

1. Vá para a loja.

1. Na barra de pesquisa, digite uma string que contenha um hífen, por exemplo &quot;WS-M-Blue&quot;.

<u>Resultado esperado:</u>

Retorna somente WS-M-Blue.

<u>Resultado real:</u>

Retorna todas as SKUs que começam com &quot;WS&quot;.

## Detalhes do patch

O patch MDVA-28993 contém as seguintes correções e melhorias:

* implementa a nova funcionalidade &quot;O mínimo deve corresponder&quot; e a pesquisa parcial pelo mecanismo Elasticsearch. Para obter detalhes sobre a configuração, consulte [Configuração da pesquisa no catálogo](https://docs.magento.com/user-guide/catalog/search-configuration.html#step-4-configure-minimum-terms-to-match) em nosso guia do usuário.
* pesquisa parcial de Elasticsearch
* corrige o problema &quot;pesquisas com hífen&quot; descrito acima.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.

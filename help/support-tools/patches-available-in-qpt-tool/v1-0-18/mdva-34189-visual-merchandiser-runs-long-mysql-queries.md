---
title: "MDVA-34189: O Visual Merchandiser executa longas consultas MySQL"
description: O patch MDVA-34189 resolve o problema em que o Adobe Commerce executa grandes consultas de Merchandiser visuais ao carregar a página de categoria de Administrador.
exl-id: 94143d80-3240-4a18-890d-fb759ea9c30d
feature: Categories, Merchandising, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-34189: Merchandiser visual executa longas consultas MySQL

O patch MDVA-34189 resolve o problema em que o Adobe Commerce executa grandes consultas de Merchandiser visuais ao carregar a página de categoria de Administrador.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalada. A ID do patch é MDVA-34189. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.4-2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O site executa grandes consultas MySQL no servidor de produção.

<u>Etapas a serem reproduzidas</u>:

1. Para acessar o Visual Merchandiser, acesse a barra lateral *Admin*, clique em **Catálogo** > **Categorias**.
1. Carregue a página **Categorias** no painel Admin (o carregamento da categoria raiz inicial) e observe as consultas executadas.

<u>Resultado esperado</u>:

A página **Categorias** do administrador deve ser carregada sem gerar consultas lentas.

<u>Resultado real</u>:

Isso depende da sua configuração do PHP. O exemplo mais comum desse erro é que a página **Categorias** não abre e um erro *Erro 503 primeiro tempo limite de byte* é exibido.

Como alternativa, quando o Adobe Commerce carrega o Visual Merchandiser, ele executa uma consulta MySQL lenta. Esta consulta inclui muitas IDs de produtos inseridas em `ORDER BY FIELD(`e`.`entity_id`,  ...)`

em `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis em QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

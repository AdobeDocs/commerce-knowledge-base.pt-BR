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

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.18 está instalado. A ID do patch é MDVA-34189. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.4-2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O site executa grandes consultas MySQL no servidor de produção.

<u>Etapas a serem reproduzidas</u>:

1. Para acessar o Visual Merchandiser, acesse o *Admin* barra lateral, clique **Catálogo** > **Categorias**.
1. Carregue o **Categorias** no painel Admin (o carregamento inicial da categoria raiz) e observe as consultas executadas.

<u>Resultado esperado</u>:

O administrador **Categorias** A página deve ser carregada sem gerar consultas lentas.

<u>Resultado real</u>:

Isso depende da sua configuração do PHP. O exemplo mais comum desse erro é que a variável **Categorias** A página não abre e um erro *Erro 503 primeiro byte tempo limite* é exibido.

Como alternativa, quando o Adobe Commerce carrega o Visual Merchandiser, ele executa uma consulta MySQL lenta. Esta consulta inclui muitas IDs de produto inseridas no `ORDER BY FIELD(`e`.`entity_id`,  ...)`

in `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.

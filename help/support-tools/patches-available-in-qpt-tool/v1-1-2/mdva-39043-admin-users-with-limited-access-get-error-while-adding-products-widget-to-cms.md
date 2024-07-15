---
title: "MDVA-39043: Os usuários administradores obtêm erro ao adicionar o widget à página do CMS"
description: O patch MDVA-39043 corrige o problema em que usuários administradores com acesso limitado recebem um erro ao adicionar o widget "Produtos" à página CMS. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 está instalada. A ID do patch é MDVA-39043. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043: Erro dos usuários administradores ao adicionar widget à página CMS

O patch MDVA-39043 corrige o problema em que usuários administradores com acesso limitado recebem um erro ao adicionar o widget &quot;Produtos&quot; à página CMS. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 está instalada. A ID do patch é MDVA-39043. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.4.3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários administradores com acesso limitado recebem um erro ao adicionar o widget &quot;Produtos&quot; à página CMS.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no back-end usando o administrador com acesso somente para editar conteúdo.
1. Ir para **Conteúdo** > **Páginas**.
1. Abra qualquer página para editar.
1. Edite o conteúdo com o **Page Builder**.
1. Adicionar widget do **Produto** da seção **Adicionar conteúdo**.
1. Clique em **Configurar** no widget do **Produto**.

<u>Resultados esperados</u>:

Nenhum erro é exibido.

<u>Resultados reais</u>:

A seguinte mensagem de erro é recebida:

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

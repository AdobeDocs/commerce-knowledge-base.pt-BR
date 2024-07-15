---
title: "MDVA-40619: As alterações de hierarquia quebram a edição em linha da página do CMS e geram um erro 500"
description: O patch MDVA-40619 resolve o problema em que a hierarquia de páginas do CMS altera a edição em linha da página do CMS e emite "erro 500". Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 está instalada. A ID do patch é MDVA-40619. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: c003d845-1ba0-49c0-9f1a-a4b0ec00f30c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40619: as alterações de hierarquia quebram a edição em linha da página do CMS e geram um erro 500

O patch MDVA-40619 resolve o problema em que a hierarquia de páginas do CMS altera a edição em linha da página do CMS e emite &quot;erro 500&quot;. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 está instalada. A ID do patch é MDVA-40619. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As alterações na hierarquia de página do CMS quebram a edição em linha da página do CMS e geram &quot;erro 500&quot;.

<u>Etapas a serem reproduzidas</u>:

1. Vá para Painel de Administração > **Conteúdo** > **Hierarquia**.
1. Selecione &quot;Exibição de loja padrão&quot;.
1. Desmarque &quot;Usar a hierarquia do nó principal&quot;.
1. Selecione a página manualmente e clique em **Salvar**.
1. Em Seguida, Vá Para **Conteúdo** > **Páginas**.
1. Tente editar qualquer página CMS na grade.
1. Clique em **Salvar**.

<u>Resultados esperados</u>:

A página foi salva com sucesso.

<u>Resultados reais</u>:

Você recebe o seguinte erro:

*Um problema técnico com o servidor criou um erro. Tente novamente para continuar o que estava fazendo. Se o problema persistir, tente novamente mais tarde.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

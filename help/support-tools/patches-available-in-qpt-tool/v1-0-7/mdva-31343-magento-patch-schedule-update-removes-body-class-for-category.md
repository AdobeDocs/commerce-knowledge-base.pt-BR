---
title: "Patch MDVA-31343: a atualização do agendamento remove a classe body da categoria"
description: O patch MDVA-31343 corrige o problema em que a classe CSS do corpo de layout atribuído para uma categoria é removida durante a atualização agendada. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. O problema está programado para ser corrigido no Adobe Commerce 2.4.2.
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Correção do MDVA-31343: a atualização do agendamento remove a classe body da categoria

O patch MDVA-31343 corrige o problema em que a classe CSS do corpo de layout atribuído para uma categoria é removida durante a atualização agendada. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. O problema está programado para ser corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A classe de corpo de layout é removida da categoria após a atualização programada.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Commerce, crie uma categoria.
1. Definir **Layout** = *Categoria — Largura total* na seção **Design**.
1. Salve a categoria.
1. Ir para a página de front-end da categoria. No aviso de origem da página, a variável

   ```css
   page-layout-category-full-width
   ```

   Classe CSS.
1. Em **CATÁLOGO** > **Categoria**, clique em **Agendar nova atualização** na seção *Alterações agendadas* para a nova categoria.
1. Aguarde o início da atualização agendada, execute cron e limpe o cache.
1. Vá para a página de categoria no front-end e inspecione a origem da página.

<u>Resultados esperados</u>:

No corpo da página, você verá a

```css
page-layout-category-full-width
```

Classe CSS.

<u>Resultados reais</u>:

No corpo da página, você verá a

```css
page-layout-2columns-left
```

Classe CSS, que é o padrão da página de categoria.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

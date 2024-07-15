---
title: "MDVA-38468: Receber uma mensagem de erro ao salvar a página do CMS"
description: 'O patch do MDVA-38468 Adobe Commerce corrige o problema em que os usuários recebem a mensagem de erro: *Já existe um item com a mesma ID "PAGE_ID"* ao salvar uma página CMS. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 está instalada. A ID do patch é MDVA-38468. Observe que o problema foi corrigido no Adobe Commerce 2.3.6.'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468: Receber uma mensagem de erro ao salvar a página CMS

O patch do MDVA-38468 Adobe Commerce corrige o problema em que os usuários recebem a mensagem de erro: *Já existe um item com a mesma ID &quot;PAGE_ID&quot;* ao salvar uma página CMS. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 está instalada. A ID do patch é MDVA-38468. Observe que o problema foi corrigido no Adobe Commerce 2.3.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
Adobe Commerce na infraestrutura em nuvem 2.3.2-p2

**Compatível com as versões do Adobe Commerce:**
Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.2-2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao tentar salvar uma página do CMS, você receberá a seguinte mensagem de erro: *Já existe um item com a mesma ID &quot;PAGE_ID&quot;.*

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo site + Store + Storeview.
1. Crie mais um site + Store + Storeview.
1. Vá para **Conteúdo** > **Hierarquia** > Adicionar qualquer página CMS existente à árvore hierárquica.
1. Ir para **Conteúdo** > **Páginas** > **Adicionar nova página**:
   * Adicione qualquer título.
   * Em Página na seção Sites, atribua a ambas as Storeview criadas.
   * Na seção Hierarquia, atribua a qualquer categoria.
   * **Salvar e Continuar Edição**.

<u>Resultados esperados</u>:

A página é salva sem erros.

<u>Resultados reais</u>:

A página é salva, mas você recebe a seguinte mensagem de erro: *Já existe um item (Magento\VersionsCms\Model\Hierarchy\Node) com a mesma ID &quot;PAGE_ID&quot;.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

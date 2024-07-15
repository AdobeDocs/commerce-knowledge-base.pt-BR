---
title: "MDVA-23845: não é possível visualizar o modelo de email quando a minificação JS está habilitada"
description: O patch de Magento MDVA-23845 corrige o problema quando não é possível visualizar o modelo de email no Admin quando a minificação JS está ativada.
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-23845: não é possível visualizar o modelo de email quando a minificação JS está habilitada

O patch de Magento MDVA-23845 corrige o problema quando não é possível visualizar o modelo de email no Admin quando a minificação JS está ativada.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-23845. Observe que o problema foi corrigido no Magento versão 2.3.5.

## Produtos e versões afetados

**O patch é criado para a versão do Magento:** Magento Commerce Cloud 2.3.3

**Compatível com as versões de Magento:** Magento Commerce e Commerce Cloud Magneto 2.3.2-2.3.4-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Habilitar a **minificação de JS** em **Admin > Lojas > Configuração > Configurações do JavaScript > Minificar Arquivos do JavaScript** = *Sim*.
1. Alternar Magento para modo de produção.
1. Vá para **Admin > Marketing > Comunicações > Modelos de email** .
1. Clique em **Adicionar Novo Modelo**.
1. Selecione o modelo **Novo Pedido**.
1. Clique no botão **Carregar Modelo**.
1. Preencha **Nome do Modelo** com **Novo Pedido.**
1. Clique no botão **Salvar Modelo**.
1. Na grade de modelos de email, clique no link **Visualizar** na coluna **Ações**.

<u>Resultados esperados</u>:

A pré-visualização do template de email aparece na janela pop-up aberta, conforme esperado.

<u>Resultados reais</u>:

A pré-visualização do modelo de email não é exibida na janela pop-up aberta. A janela pop-up está vazia e erros de JS podem ser exibidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do seu produto Magento:

* Magento Commerce: DevDocs [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) .
* Magento Commerce Cloud: DevDocs [Atualizações e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique o problema de Magento com a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

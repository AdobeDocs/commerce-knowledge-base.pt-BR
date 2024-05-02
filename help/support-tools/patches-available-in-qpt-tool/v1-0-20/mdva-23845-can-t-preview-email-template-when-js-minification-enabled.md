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

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.20 está instalado. A ID do patch é MDVA-23845. Observe que o problema foi corrigido no Magento versão 2.3.5.

## Produtos e versões afetados

**O patch é criado para a versão do Magento:** Magento Commerce Cloud 2.3.3

**Compatível com as versões do Magento:** Commerce Cloud Magento Commerce e Magneto 2.3.2-2.3.4-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u> :

1. Ativar **Minificação de JS** in **Admin > Lojas > Configuração > Configurações do JavaScript > Reduzir arquivos JavaScript** = *Sim* .
1. Alternar Magento para modo de produção.
1. Ir para **Administração > Marketing > Comunicações > Modelos de email** .
1. Clique em **Adicionar novo modelo** .
1. Selecione o **Novo pedido** modelo.
1. Clique em **Carregar modelo** botão.
1. Preencher **Nome do modelo** com **Novo pedido.**
1. Clique em **Salvar modelo** botão.
1. Na grade de modelos de email, clique em **Visualizar** no **Ações** coluna.

<u>Resultados esperados</u> :

A pré-visualização do template de email aparece na janela pop-up aberta, conforme esperado.

<u>Resultados reais</u> :

A pré-visualização do modelo de email não é exibida na janela pop-up aberta. A janela pop-up está vazia e erros de JS podem ser exibidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do seu produto Magento:

* Magento Commerce: DevDocs [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) .
* Magento Commerce Cloud: DevDocs [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Verifique o problema de Magento com a Ferramenta de correção de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.

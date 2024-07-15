---
title: "Patch MDVA-33614: não é possível salvar a página Termos"
description: '"O patch MDVA-33614 corrige o problema em que é impossível salvar edições na página Termos, porque o Page Builder lança o seguinte erro: *Ocorreu um erro ao iniciar o Page Builder. Consulte seu contato de suporte técnico*. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-33614. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.'''
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Correção MDVA-33614: não é possível salvar a página Termos

O patch MDVA-33614 corrige o problema em que é impossível salvar edições na página Termos, porque o Page Builder lança o seguinte erro: *Ocorreu um erro ao iniciar o Page Builder. Consulte seu contato de suporte técnico*. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-33614. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:** Adobe Commerce local e Adobe Commerce na infraestrutura em nuvem 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

É impossível salvar edições na página Termos porque o Page Builder emite um erro.

<u>Etapas a serem reproduzidas</u>:

1. No Commerce Admin, vá para **CONTENT** > Elements > **Pages**.
1. Selecione a página Termos.
1. Clique em **Editar**.
1. Faça uma edição e clique em **Salvar**.

<u>Resultado esperado</u>:

A página é salva sem erros.

<u>Resultado real</u>:

O seguinte erro é exibido: *Ocorreu um erro ao iniciar o Page Builder. Consulte seu contato de suporte técnico*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis em QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

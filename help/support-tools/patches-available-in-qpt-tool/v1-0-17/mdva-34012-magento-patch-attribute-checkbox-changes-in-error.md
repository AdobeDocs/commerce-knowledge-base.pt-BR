---
title: "Patch MDVA-34012: alterações da caixa de seleção de atributo no erro"
description: O patch MDVA-34012 resolve o problema em que a caixa de seleção de um atributo é alterada após uma atualização de agendamento com erro.
exl-id: 1a8f1bea-9b6a-4984-b9f0-b2b9ceb6688f
feature: Attributes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Correção do MDVA-34012: alterações da caixa de seleção de atributo no erro

O patch MDVA-34012 resolve o problema em que a caixa de seleção de um atributo é alterada após uma atualização de agendamento com erro.

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.17 está instalado. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.1 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Admin e acesse **Catálogo > Produtos**.
1. Edite qualquer produto simples.
1. Alterar a exibição de loja para uma exibição de loja específica.
1. Salve o produto com a **Usar valor padrão** caixa de seleção marcada para um atributo (Exemplo: **Ativar produto** atributo).
1. Clique em **Agendar nova atualização** para agendar algumas alterações (Exemplo: **Preço** ou **Preço especial** para uma exibição de loja específica).
1. Aguarde até que as alterações sejam concluídas.
1. Verifique o produto. Ela deve ter a caixa de seleção desmarcada e deve ter um valor de atributo de armazenamento específico.

<u>Resultados esperados</u>:

A caixa de seleção do atributo deve permanecer a mesma e não é alterada após a atualização programada, conforme esperado.

<u>Resultados reais</u>:

A caixa de seleção do atributo é alterada após a atualização do agendamento.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.

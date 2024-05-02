---
title: '"MDVA-44887: erro "Uncaught SyntaxError: Unexpected token const" no painel Admin"'
description: "O patch MDVA-44887 corrige o problema em que o usuário administrador não pode clicar em nenhuma opção de menu. O erro *Uncaught SyntaxError: Unexpected token const* é exibido no painel Admin. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 está instalada. A ID do patch é MDVA-44887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5."
exl-id: 66555e66-49d0-4f80-8f77-84ee107ab12e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44887: erro &quot;Uncaught SyntaxError: Unexpected token const&quot; no painel Admin

O patch MDVA-44887 corrige o problema em que o usuário administrador não pode clicar em nenhuma opção de menu. A variável *SyntaxError não capturado: const de token inesperado* é exibido no painel Admin. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.15 está instalado. A ID do patch é MDVA-44887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador não pode clicar em nenhuma opção de menu. A variável *SyntaxError não capturado: const de token inesperado* é exibido no painel Admin.

<u>Etapas a serem reproduzidas</u>:

1. Habilite o agrupamento JS.
1. Reduza os arquivos JS.
1. Faça logon no painel de Administração do Commerce.

<u>Resultados esperados</u>:

O usuário administrador não pode clicar em nenhuma opção de menu. Há um erro no console do navegador: *SyntaxError não capturado: const de token inesperado*.

<u>Resultados reais</u>:

O painel Administração pode ser acessado por um usuário administrador.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

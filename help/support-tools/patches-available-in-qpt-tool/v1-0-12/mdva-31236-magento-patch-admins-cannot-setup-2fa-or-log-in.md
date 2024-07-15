---
title: "MDVA-31236: administradores não podem configurar 2FA ou fazer logon"
description: O patch MDVA-31236 corrige o problema em que os usuários administradores do Commerce com acesso a recursos personalizados não podem configurar [autenticação de dois fatores (2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) ou fazer logon. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalada.
exl-id: b75d7a19-3c17-4389-b359-7aeeb8797539
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# MDVA-31236: administradores não podem configurar 2FA ou fazer logon

O patch MDVA-31236 corrige o problema em que os usuários administradores do Commerce com acesso a recursos personalizados não podem configurar a [autenticação de dois fatores (2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) ou fazer logon. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalada.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.4.0.

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local e Adobe Commerce na infraestrutura de nuvem 2.4.0-2.4.1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários sem privilégios de administrador não podem configurar seu acesso pessoal ao 2FA no momento. O 2FA conforme implementado no Adobe Commerce inclui duas funções de ACL. Uma função afeta a configuração global do sistema e é necessária somente ao configurar o sistema. A segunda função da ACL afeta contas 2FA de usuário individuais. Um usuário administrador precisa configurar esse segundo tipo de ACL 2FA.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

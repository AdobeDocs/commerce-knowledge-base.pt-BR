---
title: 'Erro "MDVA-40311: "Chave de formulário ou segurança inválida" após fazer logon no Administrador se o caminho de administrador personalizado estiver configurado"'
description: '"O patch MDVA-40311 corrige o problema em que o usuário administrador recebe uma mensagem de erro: *Chave de segurança ou formulário inválida. Atualize a página* após fazer logon no Administrador se o caminho de administração personalizado estiver configurado e a chave secreta estiver ativada. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 está instalada. A ID do patch é MDVA-40311. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.'''
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: Erro &quot;Chave de formulário ou segurança inválida&quot; após fazer logon no Administrador se o caminho de administrador personalizado estiver configurado

O patch MDVA-40311 corrige o problema em que o usuário administrador recebe uma mensagem de erro: *Chave de formulário ou segurança inválida. Atualize a página* após fazer logon no Administrador se o caminho de administração personalizado estiver configurado e a chave secreta estiver habilitada. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 está instalada. A ID do patch é MDVA-40311. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador recebe uma mensagem de erro: *Chave de formulário ou segurança inválida. Atualize a página* após fazer logon no Administrador se o caminho de administração personalizado estiver configurado e a chave secreta estiver habilitada.

<u>Etapas a serem reproduzidas</u>:

* Efetue login como o usuário Administrador usando um nome de usuário e senha válidos.

<u>Resultados esperados</u>:

O usuário pode fazer logon sem nenhuma mensagem de erro.

<u>Resultados reais</u>:

*Chave de formulário ou segurança inválida. A mensagem de erro da página* é exibida.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

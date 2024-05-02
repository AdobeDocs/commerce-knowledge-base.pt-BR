---
title: 'MDVA-42269: o usuário administrador não pode fazer logon no Admin devido ao erro "TypeError"'
description: O patch MDVA-42269 corrige o problema em que os usuários Administradores não conseguem fazer logon no Administrador devido a TypeError. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 está instalada.  A ID do patch é MDVA-42269.  A última atualização de patch está em QPT 1.1.15. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 66d744a2-054e-493c-a060-9ed78447e35b
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42269: O usuário administrador não consegue fazer logon no Admin devido ao erro &quot;TypeError&quot;

O patch MDVA-42269 corrige o problema em que os usuários Administradores não conseguem fazer logon no Administrador devido a TypeError. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.11 está instalado.  A ID do patch é MDVA-42269.  A última atualização de patch está em QPT 1.1.15. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1, 2.3.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1 - 2.4.3-p2, 2.3.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários administradores não podem fazer logon no Administrador devido ao seguinte erro: *TypeError: strtotime() espera que o parâmetro 1 seja uma sequência de caracteres, nulo fornecido.*

<u>Etapas a serem reproduzidas</u>:

Faça logon no Commerce Admin.

<u>Resultados esperados</u>:

O usuário administrador pode fazer logon com o nome de usuário e a senha corretos.

<u>Resultados reais</u>:

O usuário administrador não consegue fazer logon. O seguinte erro é registrado: *TypeError: strtotime() espera que o parâmetro 1 seja uma sequência de caracteres, nulo fornecido.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

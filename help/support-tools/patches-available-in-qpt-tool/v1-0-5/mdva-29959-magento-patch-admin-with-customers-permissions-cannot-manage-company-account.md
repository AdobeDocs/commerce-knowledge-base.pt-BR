---
title: '"Patch MDVA-29959: o administrador com permissões de "Clientes" não pode gerenciar a conta da empresa"'
description: O patch MDVA-29959 disponível na ferramenta [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versão 1.0.5 corrige o problema em que um usuário administrador restrito com todas as permissões para ACL de "Cliente" não pode gerenciar empresas (adicionar ou excluir uma empresa). Observe que o problema foi corrigido no B2B para Adobe Commerce 2.3.4.
exl-id: ee246380-d37e-4c24-8435-97ae80088227
feature: Admin Workspace, B2B, Companies, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Correção do MDVA-29959: o administrador com permissões de &quot;Clientes&quot; não pode gerenciar a conta da empresa

patch do MDVA-29959 disponível no [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) a ferramenta versão 1.0.5 corrige o problema em que um usuário administrador restrito com todas as permissões para ACL de &quot;Cliente&quot; não pode gerenciar empresas (adicionar ou excluir uma empresa). Observe que o problema foi corrigido no B2B para Adobe Commerce 2.3.4.

## Produtos e versões afetados

B2B para Adobe Commerce na infraestrutura em nuvem 2.3.0-2.3.3-p1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador com todas as permissões para a ACL &quot;Cliente&quot; não pode gerenciar empresas (adicionar ou excluir uma empresa).

<u>Etapas a serem reproduzidas</u>

1. No Administrador do Commerce, crie uma nova função de administrador e atribua um usuário a essa função.
1. Atribuir à função somente recursos de &quot;Cliente&quot;.
1. Efetue logon como um usuário com esta função.
1. Tente excluir uma conta de empresa.

<u>Resultado esperado:</u>

A conta da empresa foi excluída com sucesso.

<u>Resultado real:</u>

Não é possível excluir a conta da empresa. Você recebe a *Você precisa de permissões para visualizar este conteúdo.* mensagem de erro.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

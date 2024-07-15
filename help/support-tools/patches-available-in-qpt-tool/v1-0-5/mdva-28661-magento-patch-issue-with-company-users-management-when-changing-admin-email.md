---
title: "MDVA-28661: problema com o gerenciamento de usuários da empresa ao alterar o email do administrador"
description: O patch MDVA-28861 corrige o problema em que os usuários recebem um erro ao alterar o email do administrador. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada. A ID do patch é MDVA-28861.
exl-id: 2d6691e5-baaf-4cef-ae7e-2b6ccc7f2cd3
feature: Admin Workspace, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28661: problema com o gerenciamento de usuários da empresa ao alterar o email do administrador

O patch MDVA-28861 corrige o problema em que os usuários recebem um erro ao alterar o email do administrador. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada. A ID do patch é MDVA-28861.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.0 a 2.4.1 (incluindo 2.3.5-p1) com extensão B2B

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Após alterar o endereço de email do **Administrador da Empresa**, um erro é retornado e a lista de **Usuários da Empresa** não é exibida.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar a funcionalidade Empresa (Saiba mais sobre isso em [Instalar B2B: habilite os recursos B2B no Administrador do Commerce](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) em nossa documentação do desenvolvedor e crie uma nova Empresa com dois usuários, um administrador e dois usuários, todos com endereços de email).
1. Vá para o **Administrador do Commerce** > **Clientes** > **Empresas** e abra a conta da sua Empresa.
1. Abra a guia **Administrador da Empresa** e altere o administrador para o primeiro usuário, o que inclui a alteração do email **Administrador da Empresa** para o email do primeiro usuário.
1. Acesse o front-end do Adobe Commerce e faça logon como o primeiro usuário.
1. Vá para a seção **Usuários da Empresa**.

<u>Resultados esperados</u>:

A lista **Usuários da Empresa** deve ser exibida conforme esperado.

<u>Resultados reais</u>:

A lista **Usuários da Empresa** não é exibida e um erro semelhante ao seguinte é exibido:

```bash
No such entity with id = 2
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

Para saber mais sobre a funcionalidade da empresa B2B, consulte estes artigos em nossa documentação do desenvolvedor:

* [Guia do desenvolvedor B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Gerenciar funções da empresa](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Referência de caminhos de configuração da Extensão B2B do Adobe Commerce Enterprise](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)

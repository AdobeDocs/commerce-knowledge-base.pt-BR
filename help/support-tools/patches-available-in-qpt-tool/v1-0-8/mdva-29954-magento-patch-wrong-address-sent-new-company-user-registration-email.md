---
title: "MDVA-29954: endereço incorreto enviado novo email de registro de usuário da empresa"
description: O patch MDVA-29954 resolve o problema em que os emails "Nova solicitação de registro da empresa" e "Você foi vinculado a uma empresa" são enviados do endereço de email errado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 9b3d1b93-3fe6-40a0-a68a-3e3d789c6d66
feature: B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29954: endereço errado enviado novo email de registro de usuário da empresa

O patch MDVA-29954 resolve o problema em que os emails &quot;Nova solicitação de registro da empresa&quot; e &quot;Você foi vinculado a uma empresa&quot; são enviados do endereço de email errado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.3.5-p2, 2.4.0 e 2.4.1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisitos</u>:

Instale o Adobe Commerce com B2B, com **Recursos B2B** e **Empresa** habilitados.

<u>Etapas a serem reproduzidas</u>:

1. Clique na lista suspensa **Criar Conta** na loja e selecione **Criar Nova Conta de Empresa**.
1. Preencha os campos obrigatórios e registre a conta.
1. Habilite a **Empresa** do back-end (**Cliente** > **Empresas**).
1. Verifique o endereço de email que você usou para o registro.
1. Defina a **senha do Administrador da Empresa** seguindo as instruções enviadas por email.
1. Faça logon no front-end com a **senha de Administrador da Empresa**.
1. Crie um novo **Usuário da Empresa** em **Minha Conta** > **Usuários da Empresa** > **Adicionar Novo Usuário**.
1. Vá para **Lojas** > **Configurações** > **Endereços de Email de Repositório Geral** > **Contato Geral** e verifique o **Email do Remetente**.
1. Vá para o email que você usou para registrar o **Novo Usuário** na Etapa 7.

<u>Resultados esperados</u>:

O email &quot;Você foi vinculado a uma empresa&quot; é enviado de um endereço de email com o mesmo valor do **Email do Remetente** na Etapa 8.

<u>Resultados reais</u>:

O email &quot;Você foi vinculado a uma empresa&quot; é enviado do email **Administrador de Empresas**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

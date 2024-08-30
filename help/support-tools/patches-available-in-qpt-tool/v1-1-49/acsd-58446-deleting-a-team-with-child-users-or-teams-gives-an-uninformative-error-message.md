---
title: "ACSD-58446: excluir uma equipe com usuários ou equipes secundárias por meio do GraphQL fornece uma mensagem de erro não informativa"
description: Aplique o patch ACSD-58446 para corrigir o problema do Adobe Commerce em que a exclusão de uma equipe com usuários ou equipes secundários por meio do GraphQL retorna uma mensagem de erro não informativa inconsistente com a interface do usuário.
feature: Product, GraphQL, Company
role: Admin, Developer
source-git-commit: ab290f7c5b052aa220b3ef003febd9afc1cfdf00
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-58446: excluir uma equipe com usuários ou equipes secundárias por meio do GraphQL gera uma mensagem de erro não informativa

O patch ACSD-58446 corrige o problema do Adobe Commerce, em que a exclusão de uma equipe com usuários ou equipes secundários por meio do GraphQL retorna uma mensagem de erro não informativa inconsistente com a interface do usuário. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 está instalado. A ID do patch é ACSD-58446. Observe que o problema está programado para ser corrigido no Adobe Commerce B2B 1.5.1

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce e do Magento Open Source:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Excluir uma equipe com usuários ou equipes filhos por meio do GraphQL retorna uma mensagem de erro não informativa inconsistente com a interface do usuário.

## Pré-condições:

Módulos B2B instalados.

<u>Etapas a serem reproduzidas</u>:

1. Habilite a funcionalidade *[!UICONTROL Company]*.
1. Crie uma nova conta da empresa.
1. Faça logon no **[!UICONTROL Admin]** e torne a conta da empresa ativa.
1. Verifique o email e defina uma senha para a nova conta da empresa.
1. Crie uma nova equipe para a empresa.
1. Faça login como o **[!UICONTROL company user]** no front-end e adicione um **[!UICONTROL new user]** para a equipe criada.
1. Faça logon no **[!UICONTROL Admin]**, desabilite o usuário da empresa e defina *[!UICONTROL Customer Active]* = *Não*
1. Exclua a equipe criada por meio do GraphQL.

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>Resultados esperados</u>:

Uma mensagem de erro informativa consistente com a interface do usuário é retornada.

<u>Resultados reais</u>:

Uma mensagem de erro interna genérica do servidor é retornada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

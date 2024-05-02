---
title: '"ACSD-47027: consulta B2B lenta [!UICONTROL CompanyRole] [!DNL GraphQL] atualizar'''
description: Aplique o patch ACSD-47027 para corrigir o problema do Adobe Commerce em que há uma consulta B2B lenta [!UICONTROL CompanyRole] [!DNL GraphQL] atualização.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: consulta B2B lenta [!UICONTROL CompanyRole] [!DNL GraphQL] atualizar

O patch ACSD-47027 resolve o problema em que a consulta lenta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] A atualização do não funciona conforme o esperado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.23 está instalado. A ID do patch é ACSD-47027. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A consulta lenta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] A atualização do não funciona conforme o esperado.

<u>Pré-requisitos</u>:

Instale o módulo B2B.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Adobe Commerce, acesse **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** e defina **[!UICONTROL Enable Company]** para _Sim_.
1. Acesse o front-end e crie uma empresa.
1. Depois de fazer logon como usuário da empresa, acesse **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** e adicionar uma nova função.
1. Ativar [!UICONTROL dev] log de consulta usando `bin/magento dev:que:enab`.
1. Agora envie o exemplo abaixo [!DNL GraphQL] solicitação (a id é a [!UICONTROL base64] id de função codificada):

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. Verifique o log de consulta.
1. Você pode ver que a consulta acima é executada. Esta consulta é executada em `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Resultados esperados</u>:

A variável `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` precisa ser otimizada para evitar o carregamento de todos os dados disponíveis na **[!UICONTROL company_permissions]** Tabela DB.

<u>Resultados reais</u>:

O Adobe Commerce executa uma consulta sem nenhum filtro. Quando há um grande número de registros, leva muito tempo para o Adobe Commerce preparar a coleta de dados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor. 

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

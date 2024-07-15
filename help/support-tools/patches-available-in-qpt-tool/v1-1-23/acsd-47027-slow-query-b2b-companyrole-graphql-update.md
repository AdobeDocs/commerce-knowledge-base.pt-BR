---
title: '"ACSD-47027: atualização de consulta B2B lenta"[!UICONTROL CompanyRole] [!DNL GraphQL] '
description: Aplique o patch ACSD-47027 para corrigir o problema do Adobe Commerce em que há uma atualização de consulta B2B [!UICONTROL CompanyRole] [!DNL GraphQL]  lenta.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: atualização de [!DNL GraphQL] de B2B de consulta lenta [!UICONTROL CompanyRole]

O patch ACSD-47027 resolve o problema em que a atualização de consulta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] lenta não funciona como esperado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 está instalado. A ID do patch é ACSD-47027. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A atualização de consulta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] lenta não funciona como esperado.

<u>Pré-requisitos</u>:

Instale o módulo B2B.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Adobe Commerce, vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** e defina **[!UICONTROL Enable Company]** como _Sim_.
1. Acesse o front-end e crie uma empresa.
1. Depois de fazer logon como usuário da empresa, vá para **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** e adicione uma nova função.
1. Habilitar log de consultas [!UICONTROL dev] usando `bin/magento dev:que:enab`.
1. Agora envie a solicitação [!DNL GraphQL] abaixo (a ID é a ID de função codificada [!UICONTROL base64]):

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

O `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` precisa ser otimizado para evitar o carregamento de todos os dados disponíveis na tabela de BD **[!UICONTROL company_permissions]**.

<u>Resultados reais</u>:

O Adobe Commerce executa uma consulta sem nenhum filtro. Quando há um grande número de registros, leva muito tempo para o Adobe Commerce preparar a coleta de dados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor. 

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

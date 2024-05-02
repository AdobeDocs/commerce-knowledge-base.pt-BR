---
title: '"ACSD-51739: Erro ao solicitar "structure_id" na solicitação do GraphQL "CompanyTeam"'
description: Aplique o patch ACSD-51739 para corrigir o problema do Adobe Commerce em que um erro é retornado quando o "structure_id" é solicitado em uma solicitação do GraphQL "CompanyTeam".
exl-id: 31c085e0-c8be-4709-9620-80ff360dca9a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739: erro na solicitação `structure_id` in `CompanyTeam` solicitação GraphQL

O patch ACSD-51739 corrige o problema em que um erro é retornado quando a variável `structure_id` é solicitado em uma `CompanyTeam` solicitação GraphQL. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.34 está instalado. A ID do patch é ACSD-51739. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um erro é retornado quando a variável `structure_id` é solicitado em uma `CompanyTeam` solicitação GraphQL.

<u>Etapas a serem reproduzidas</u>

1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** e defina *[!UICONTROL Enable Company]* para *Sim*.
1. Crie uma empresa junto com um usuário administrador de empresa.
1. Criar um novo cliente (*customer1*) e atribua a empresa (criada acima) a esse cliente.
1. No front-end, faça logon como o usuário administrador da empresa.
1. Criar uma equipe da empresa e atribuir *customer1* ao grupo usando a função arrastar e soltar.
1. Execute a seguinte consulta GraphQl de empresa, que inclui `CompanyTeam` com `structure_id`:

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. Verifique a resposta do GraphQL.

<u>Resultados esperados</u>:

Nenhum erro é retornado e todos os dados solicitados estão presentes na resposta do GraphQL.

<u>Resultados reais</u>:

* A resposta contém um *Erro interno do servidor*.
* `var/log/exception.log` contém:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

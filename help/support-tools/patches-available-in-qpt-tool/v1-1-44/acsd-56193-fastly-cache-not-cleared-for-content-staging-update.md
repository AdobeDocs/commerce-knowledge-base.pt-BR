---
title: "ACSD-56193: [!DNL Fastly] o cache não foi limpo para atualização de preparo de conteúdo"
description: Aplique o patch ACSD-56193 para corrigir o problema do Adobe Commerce em que o cache  [!DNL Fastly]  não é limpo para atualização de preparo de conteúdo.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: d4bbfafa-2d24-44cf-a08b-f7dd9111a65b
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-56193: o cache [!DNL Fastly] não é limpo para atualização de preparo de conteúdo

O patch ACSD-56193 corrige o problema em que o cache [!DNL Fastly] não é limpo para atualização de preparo de conteúdo. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. A ID do patch é ACSD-56193. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cache [!DNL Fastly/Varnish] não foi limpo para atualização de preparo de conteúdo

<u>Etapas a serem reproduzidas</u>:

1. Instalar e configurar o cache do [!DNL Varnish].
1. Criar um bloco estático com uma atualização agendada.
1. Crie uma categoria que incorpore o bloco estático.
1. Busque o conteúdo da categoria usando a consulta do GraphQL abaixo:

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. Execute esta consulta várias vezes e verifique se a resposta está armazenada em cache no [!DNL Varnish].
1. Execute o cron para aplicar a alteração agendada.
1. Execute a consulta do GraphQL acima novamente.
1. Crie um novo agendamento para o mesmo bloco estático.
1. Repita as etapas numeradas de 5 a 9.

<u>Resultados esperados</u>:

O conteúdo atualizado é retornado após a execução das atualizações programadas.

<u>Resultados reais</u>:

O conteúdo desatualizado é retornado após a execução das atualizações programadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

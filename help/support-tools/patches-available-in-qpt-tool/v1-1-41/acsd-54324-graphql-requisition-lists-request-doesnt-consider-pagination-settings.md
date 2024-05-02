---
title: "ACSD-54324: a solicitação requisition_lists do GraphQL não considera configurações de paginação"
description: Aplique o patch ACSD-54324 para corrigir o problema do Adobe Commerce em que a solicitação "requisition_lists" do GraphQL não considera configurações de paginação e retorna todos os resultados.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists` a solicitação não considera as configurações de paginação

O patch ACSD-54324 corrige o problema em que o GraphQL `requisition_lists` A solicitação do não considera configurações de paginação e retorna todos os resultados. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.41 está instalado. A ID do patch é ACSD-54324. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O GRAPHQL `requisition_lists` A solicitação do não considera configurações de paginação e retorna todos os resultados.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no administrador e acesse **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Definir *[!UICONTROL Enable Requisition List]* para *Sim*.

1. Faça logon no front-end e acesse **[!UICONTROL My Requisition Lists]** no menu superior ou no **[!UICONTROL My Account]** e criar várias requisições (exemplo: 7).
1. Depois de gerar um token do cliente, execute o GraphQL abaixo `requisition_lists` consulta para o cliente.

   * Certifique-se de que o tamanho da página seja menor que o número total de listas de requisições criadas por você (exemplo: 4)

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Observe que o valor de `total_count` O campo mostra 7, quando deve mostrar 4.

   O número de itens também mostra 7 quando deve ser o mesmo que o *tamanho da página*.

<u>Resultados esperados</u>:

* O número listado como *tamanho da página* é retornado em `total_count` e não o número total de registros.
* O número de itens é o mesmo que o *tamanho da página*.

<u>Resultados reais</u>:

O número total de registros é retornado em `total_count`, mesmo que *tamanho da página* é mencionado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

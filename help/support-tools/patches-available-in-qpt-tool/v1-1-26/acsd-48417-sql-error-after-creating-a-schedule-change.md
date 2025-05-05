---
title: 'ACSD-48417: Erro de SQL após criar uma alteração de agendamento'
description: Aplique o patch ACSD-48417 para corrigir o problema do Adobe Commerce em que um erro SQL é exibido após criar uma alteração de agendamento para um produto e salvar outro produto.
exl-id: 2bbf3bb5-dec8-43b3-81f1-be0dc53d1f46
feature: Storage
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-48417: Erro de SQL após criar uma alteração de agendamento

O patch ACSD-48417 corrige o problema em que um erro SQL é exibido após criar uma alteração de agendamento para um produto e salvar outro produto. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 está instalado. A ID do patch é ACSD-48417. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um erro de SQL é exibido depois de criar uma alteração de agendamento para um produto e salvar outro produto.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Magento 2.4-develop EE + Dados de amostra.
1. Vá para o painel de administração > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Edite qualquer produto (por exemplo, Apenas Duffle Bag [SKU: 24-MB01]).
1. Programar uma nova atualização:
   * Selecionar **[!UICONTROL Save as a New Update]**
   * Nome da atualização: &quot;Atualização 1&quot;
   * Data de início: hora atual +1 min
   * Data de término: hora atual +1 hora
   * Modifique o nome do produto para: &quot;Apenas Duffle Bag 2&quot;
   * Salve o produto.
1. Vá para a CLI, execute o cron e aguarde até que o cronograma seja aplicado.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. Novamente, vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e edite qualquer produto configurável (por exemplo, Chaz Kangeroo Hoodie [SKU: MH01]).

   * Desabilitar todas as variantes. Vá para a coluna Ações > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Salve o configurável.

<u>Resultados esperados</u>:

Nenhum erro ao salvar o produto.

<u>Resultados reais</u>:

Ocorre o seguinte erro:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].

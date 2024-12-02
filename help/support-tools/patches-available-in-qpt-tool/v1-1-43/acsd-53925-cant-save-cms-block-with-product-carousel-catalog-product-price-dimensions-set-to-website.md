---
title: 'ACSD-53925: Não é possível salvar o bloco CMS com [!UICONTROL Product Carousel]'
description: Aplique o patch ACSD-53925 para corrigir o problema do Adobe Commerce em que o administrador não pode salvar um bloco do CMS com o Carrossel de produtos quando o modo de dimensões para "catalog_product_price" está definido como site.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925: Não é possível salvar o bloco CMS com *[!UICONTROL Product Carousel]*

O patch ACSD-53925 corrige o problema em que o administrador não pode salvar um bloco do CMS com *[!UICONTROL Product Carousel]* quando o modo de dimensões para `catalog_product_price` está definido como site. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.43 está instalado. A ID do patch é ACSD-53925. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O administrador não pode salvar um bloco CMS com *[!UICONTROL Product Carousel]* quando o modo de dimensões para `catalog_product_price` está definido como site.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos simples:
   * simples1 - US$ 10
   * simples2 - US$ 20
1. Crie um produto de pacote &#39;*bundle1-dyn*&#39; com duas opções com base em SKUs de produtos simples.
1. Definir modo de dimensões para o indexador de preço do produto:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Vá para **[!UICONTROL Content]** > **[!UICONTROL Blocks]** e crie um novo bloco do CMS.
1. Editar o conteúdo usando [!DNL Page Builder]:
   * Adicionar um elemento *[!UICONTROL Row]*
   * Adicionar um elemento *[!UICONTROL Products]*
   * Selecionar *[!UICONTROL Product Carousel]*
   * Inserir SKU do produto - *bundle1-dyn*
1. Salve o bloco do CMS.

<u>Resultados esperados</u>:

O usuário pode adicionar um carrossel de produtos sem erros.

<u>Resultados reais</u>:

* Uma mensagem é exibida na interface do usuário: *Ocorreu um erro ao gerar este conteúdo*
* `var/log/exception.log` contém o seguinte erro:

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

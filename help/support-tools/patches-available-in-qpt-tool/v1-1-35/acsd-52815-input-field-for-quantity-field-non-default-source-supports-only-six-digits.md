---
title: "ACSD-52815: O campo de entrada para o campo de quantidade de origem não padrão suporta apenas até 6 dígitos"
description: Aplique o patch ACSD-52815 para corrigir o problema de desempenho do Adobe Commerce, em que o campo de entrada para o campo de quantidade de uma fonte não padrão suporta apenas até 6 dígitos, ao contrário de 8 para um estoque padrão.
feature: Inventory, Products
role: Admin
exl-id: 44fda5ef-cb8a-481a-9112-f36d886ae3db
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52815: O campo de entrada para o campo de quantidade de origem não-padrão suporta apenas até 6 dígitos

O patch ACSD-52815 corrige o problema em que o campo de entrada para o campo de quantidade de uma fonte não padrão suporta apenas até 6 dígitos, ao contrário de 8 para um estoque padrão. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-52815. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O campo de entrada para o campo de quantidade de uma origem não padrão suporta apenas até 6 dígitos, ao contrário de 8 para um estoque padrão.

<u>Etapas a serem reproduzidas</u>:

1. Criar um novo estoque e uma nova origem.
1. Crie um produto com o novo estoque de origem definido como 123.
1. Verifique a quantidade vendável (123).
1. Atualize a quantidade de origem para 12345678.
1. Verifique novamente a quantidade vendável.

<u>Resultados esperados</u>:

Quantidade disponível mostra o valor correto.

<u>Resultados reais</u>:

A quantidade comercializável é de 999999,9999.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

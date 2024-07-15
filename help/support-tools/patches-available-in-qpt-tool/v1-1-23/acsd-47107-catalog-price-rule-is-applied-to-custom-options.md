---
title: "ACSD-47107: a regra de preço do catálogo é aplicada às opções personalizadas"
description: Aplique o patch ACSD-47107 para corrigir o problema do Adobe Commerce em que a regra de preço de catálogo é aplicada às opções personalizadas.
exl-id: 5de2a87e-90c1-4a2a-a75c-7f9ca766868e
feature: Catalog Management, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-47107: a regra de preço do catálogo é aplicada às opções personalizadas

O patch ACSD-47107 corrige o problema em que a regra de preço do catálogo é aplicada às opções personalizadas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 está instalado. A ID do patch é ACSD-47107. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.4-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A regra de preço de catálogo é aplicada às opções personalizadas.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma regra de preço de catálogo.
1. Defina-o como *Aplicar como uma porcentagem do preço original* e adicione um desconto de 10%.
1. Selecione qualquer produto.
1. Crie algumas opções personalizadas.
1. Verifique o preço no front-end.

<u>Resultados esperados</u>:

A regra de preço de catálogo não é aplicada às opções personalizadas; ela é aplicada somente ao preço original do produto.

<u>Resultados reais</u>:

A regra de preço de catálogo é aplicada às opções personalizadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

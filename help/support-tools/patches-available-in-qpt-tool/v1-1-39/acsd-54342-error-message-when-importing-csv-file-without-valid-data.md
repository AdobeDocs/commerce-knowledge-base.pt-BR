---
title: "ACSD-54342: Mensagem de erro ao importar arquivo CSV sem dados válidos"
description: Aplique o patch ACSD-54342 para corrigir o problema do Adobe Commerce em que ocorre uma mensagem de erro incorreta ao importar um arquivo CSV sem dados válidos.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 7f443ad8-c4b7-4294-b38f-9861e221bef2
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-54342: Mensagem de erro ao importar arquivo CSV sem dados válidos

O patch ACSD-54342 corrige o problema em que uma mensagem de erro incorreta ocorre ao importar um arquivo CSV sem dados válidos. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.39 está instalado. A ID do patch é ACSD-54342. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma mensagem de erro incorreta ocorre ao importar um arquivo CSV sem dados válidos.

<u>Etapas a serem reproduzidas</u>:

1. Criar um arquivo de importação somente com dados inválidos (Exemplos: [!DNL SKUs] que não existem, campos de endereço de cliente inválidos ou endereços de email de cliente malformados).
1. Importe o arquivo, selecionando para ignorar os erros de validação.

<u>Resultados esperados</u>:

A validação falha com `There are no valid rows to import` mensagem.

<u>Resultados reais</u>:

A validação é bem-sucedida, mas a importação falha com `Error in data structure: values are mixed` mensagem.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

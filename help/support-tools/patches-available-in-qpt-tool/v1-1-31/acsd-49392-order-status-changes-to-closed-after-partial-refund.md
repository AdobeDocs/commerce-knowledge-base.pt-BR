---
title: "ACSD-49392: o status do pedido muda para fechado após o reembolso parcial"
description: Aplique o patch ACSD-49392 para corrigir o problema do Adobe Commerce em que o status do pedido muda para fechado após um reembolso parcial para um produto empacotado.
exl-id: fca6f502-e224-4444-b0d0-f823853c9458
feature: Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-49392: O status da ordem muda para fechado após reembolso parcial

O patch ACSD-49392 corrige o problema em que o status do pedido muda para fechado após um reembolso parcial para um produto empacotado. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.31 está instalado. A ID do patch é ACSD-49392. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.3.7-p4 e 2.4.1 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do pedido muda para closed após um reembolso parcial de um produto agrupado.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Adobe Commerce e crie qualquer produto empacotado ou use o produto empacotado existente.
1. Fazer um pedido com este produto agrupado com uma quantidade maior que 1.
1. Acesse o administrador e abra o pedido criado na etapa 2 em **[!UICONTROL Sales]** > **[!UICONTROL Order]** e criar uma fatura. Observe o status do pedido. Estará em processamento.
1. Criar um aviso de crédito parcial (não reembolsar para todos os produtos do pacote).
1. Verifique o status do pedido.

<u>Resultados esperados</u>

Depois de criar um aviso de crédito parcial para o produto agrupado, o status do pedido é em processamento.

<u>Resultados reais</u>

Depois de criar um aviso de crédito parcial para o produto agrupado, o status do pedido é concluído.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

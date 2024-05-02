---
title: "ACSD-49464: NFFs, entregas e avisos de crédito não movidos do arquivo"
description: Aplique o patch ACSD-49464 para corrigir o problema do Adobe Commerce em que NFFs, entregas e avisos de crédito não são movidos de volta do arquivo quando orderId é diferente.
exl-id: 845f9878-5f7e-4e58-8f8a-b02af17b3f11
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-49464: NFFs, entregas e avisos de crédito não movidos do arquivo

O patch ACSD-49464 corrige o problema em que faturas, remessas e avisos de crédito não são movidos do arquivo quando orderId é diferente. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.29 está instalado. A ID do patch é ACSD-49464. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

NFFs, entregas e avisos de crédito não são movidos de volta do arquivo quando a orderId é diferente.

<u>Etapas a serem reproduzidas</u>:

1. Ativar arquivamento de ordens, NFFs, entregas e avisos de crédito.
1. Criar e concluir um pedido, incluindo remessa, fatura e aviso de crédito.
1. Certifique-se de que as IDs de remessa, fatura e aviso de crédito não sejam iguais ao número do pedido.
1. Mova a ordem para o arquivo morto.
1. Restaurar a ordem arquivada para o gerenciamento de pedidos.
1. Verifique os detalhes da NFF, da remessa e do aviso de crédito sob os respectivos [!UICONTROL Invoice], [!UICONTROL Shipping], e [!UICONTROL Credit Memo] páginas de grade.

<u>Resultados esperados</u>:

Os registros relacionados originais são restaurados quando o pedido é movido da lista de arquivamento para o gerenciamento de pedidos.

<u>Resultados reais</u>:

* Nenhum registro para remessa, fatura e avisos de crédito se todas as IDs forem diferentes.
* Se o pedido e os registros relacionados tiverem a mesma ID, os registros serão retornados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

---
title: "ACSD-57003: O status do pedido muda para *Concluído* em vez de mudar para *Processamento*"
description: Aplique o patch ACSD-57003 para corrigir o problema do Adobe Commerce em que o status do pedido muda para *Concluído* em vez de mudar para *Processamento*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: c3c59185-c447-46fa-b404-6c4a4a300315
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-57003: o status do pedido muda para *Concluído* em vez de alterar para *Processando*

O patch ACSD-57003 corrige o problema em que o status do pedido muda para *Concluído* em vez de alterar para *Processando*. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.46 está instalado. A ID do patch é ACSD-57003. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do pedido muda para *Concluído* em vez de alterar para *Processando* quando uma ordem é parcialmente reembolsada e parcialmente entregue.

<u>Etapas a serem reproduzidas</u>:

1. Criar um pedido com dois produtos configuráveis.
1. Faturar todos os itens.
1. Entregar somente o primeiro item.
1. Reembolsar/criar um aviso de crédito apenas para o item entregue (*primeiro item*).
1. Verifique o status do pedido.

<u>Resultados esperados</u>:

O status do pedido deve estar no _Processando_ estado.

<u>Resultados reais</u>:

Alterações no status do pedido *Concluído* depois de criar um aviso de crédito para o item parcialmente entregue.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

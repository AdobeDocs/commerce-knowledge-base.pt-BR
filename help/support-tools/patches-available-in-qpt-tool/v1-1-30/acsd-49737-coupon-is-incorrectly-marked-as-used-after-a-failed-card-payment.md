---
title: "ACSD-49737: o cupom está marcado incorretamente como usado após um pagamento de cartão com falha"
description: Aplique o patch ACSD-49737 para corrigir o problema do Adobe Commerce em que o cupom é marcado incorretamente como usado após uma falha no pagamento por cartão.
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737: o cupom está marcado incorretamente como *usado* após falha no pagamento do cartão

O patch ACSD-49737 corrige o problema em que o cupom é marcado incorretamente como *usado* após falha no pagamento do cartão. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.30 está instalado. A ID do patch é ACSD-49737. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cupom está marcado incorretamente como *usado* após falha no pagamento do cartão.

<u>Pré-requisitos</u>:

1. Configure o **[!UICONTROL Braintree sandbox payment]** método.
1. Verifique se [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) consumidor está configurado e em execução.

<u>Etapas a serem reproduzidas</u>:

1. Criar um **[!UICONTROL Cart Price Rule]** com códigos de cupom gerados automaticamente.
1. Faça logon como cliente.
1. Adicionar produtos ao carrinho.
1. Aplicar um código de cupom gerado automaticamente.
1. Tente fazer um pedido com um pagamento com falha.
1. Verifique o uso do cupom no **[!UICONTROL Cart Price Rule]** no **[!UICONTROL Manage Coupon Codes]** guia.

<u>Resultados esperados</u>:

O cupom não deve ser sinalizado como *usado* se o pagamento falhar.

<u>Resultados reais</u>:

* O código do cupom diz - Usado: *Sim*, Horas Utilizadas: *1*
* O código do cupom é válido apenas para uso único.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Etapas adicionais necessárias após a instalação do patch

(Esta seção é opcional; pode haver algumas etapas necessárias após a aplicação do patch para corrigir o problema.) 

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

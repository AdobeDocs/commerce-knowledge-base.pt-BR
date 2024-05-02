---
title: "ACSD-47910: ordens, NFFs, remessas, avisos de crédito ausentes nas respectivas grades de entidade"
description: Aplique o patch ACSD-47910 para corrigir o problema do Adobe Commerce em que há ordens, NFFs, entregas e avisos de crédito ausentes nas respectivas grades de entidade.
exl-id: 4eb897ec-16e4-420e-89a6-c8f7c8740303
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-47910: ordens, NFFs, entregas e avisos de crédito ausentes nas respectivas grades de entidade

O patch ACSD-47910 corrige o problema em que há pedidos, faturas, remessas e avisos de crédito ausentes nas grades de entidades respectivas. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.25 está instalado. A ID do patch é ACSD-47910. A versão na qual esse problema será corrigido ainda não está disponível.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ordens, NFFs, entregas e avisos de crédito ausentes nas respectivas grades de entidade.

<u>Etapas a serem reproduzidas</u>:

1. Ativar **[!UICONTROL Asynchronous indexing]** em **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Faça dois pedidos.
1. Execute o cron para sincronizar essas ordens com a grade.
1. Abra um dos pedidos e prepare-o para ser faturado. NÃO ENVIAR A FATURA AINDA.
1. Faça um novo pedido pronto para ser colocado no front-end. NÃO CLIQUE NO BOTÃO FAZER PEDIDO AINDA.
1. Adicionar um `sleep(30)` no `foreach` em `NotSyncedDataProvider::L43`.
1. Executar `bin/magento cron:run`.
1. Agora faça o novo pedido.
1. Faturar a ordem anterior.
1. Execute o cron novamente, esperando que a nova ordem seja sincronizada.
1. Acesse a grade de pedidos no Admin.

<u>Resultados esperados</u>:

O novo pedido deve aparecer na grade de pedidos.

<u>Resultados reais</u>:

A atualização de pedido anterior foi sincronizada com a grade (**[!UICONTROL status: Processing]**). A nova ordem nunca aparece na grade.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

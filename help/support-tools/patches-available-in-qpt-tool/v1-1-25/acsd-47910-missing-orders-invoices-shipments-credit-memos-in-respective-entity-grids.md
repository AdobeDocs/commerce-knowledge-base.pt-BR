---
title: 'ACSD-47910: ordens, NFFs, entregas, avisos de crédito ausentes nas respectivas grades de entidade'
description: Aplique o patch ACSD-47910 para corrigir o problema do Adobe Commerce em que há ordens, NFFs, entregas e avisos de crédito ausentes nas respectivas grades de entidade.
exl-id: 4eb897ec-16e4-420e-89a6-c8f7c8740303
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-47910: ordens, NFFs, entregas e avisos de crédito ausentes nas respectivas grades de entidade

O patch ACSD-47910 corrige o problema em que há pedidos, faturas, remessas e avisos de crédito ausentes nas grades de entidades respectivas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 está instalado. A ID do patch é ACSD-47910. A versão na qual esse problema será corrigido ainda não está disponível.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ordens, NFFs, entregas e avisos de crédito ausentes nas respectivas grades de entidade.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL Asynchronous indexing]** em **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Faça dois pedidos.
1. Execute o cron para sincronizar essas ordens com a grade.
1. Abra um dos pedidos e prepare-o para ser faturado. NÃO ENVIAR A FATURA AINDA.
1. Faça um novo pedido pronto para ser colocado no front-end. NÃO CLIQUE NO BOTÃO FAZER PEDIDO AINDA.
1. Adicione um `sleep(30)` no `foreach` em `NotSyncedDataProvider::L43`.
1. Executar `bin/magento cron:run`.
1. Agora faça o novo pedido.
1. Faturar a ordem anterior.
1. Execute o cron novamente, esperando que a nova ordem seja sincronizada.
1. Acesse a grade de pedidos no Admin.

<u>Resultados esperados</u>:

O novo pedido deve aparecer na grade de pedidos.

<u>Resultados reais</u>:

A atualização da ordem anterior foi sincronizada com a grade (**[!UICONTROL status: Processing]**). A nova ordem nunca aparece na grade.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

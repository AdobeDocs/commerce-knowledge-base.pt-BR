---
title: "ACSD-57565: o painel de pedidos exibe informações de pedidos incorretas"
description: Aplique o patch ACSD-57565 para corrigir o problema do Adobe Commerce em que o painel de pedidos exibe informações incorretas sobre os pedidos até que o período seja atualizado.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 5b292fef-23f6-479f-bf76-adad53d30cf4
source-git-commit: fdf6e6e85f903a26a7b44674937ccf88ee769d06
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57565: o painel de pedidos exibe informações de pedidos incorretas

O patch ACSD-57565 corrige o problema em que o painel de pedidos exibe informações incorretas do pedido até que o período de tempo seja atualizado. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.48 está instalado. A ID do patch é ACSD-57565. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch

## Problema

O painel do pedido exibe informações incorretas do pedido.

<u>Etapas a serem reproduzidas</u>:

1. Ativar **[!UICONTROL dashboard charts]**.
1. Criar um pedido e faturar.
1. Aguarde pelo menos 24 horas após o horário de criação do pedido.
1. Verifique a **[!UICONTROL dashboard chart]** dados.
1. Anote a contagem completa de pedidos.
1. Altere a hora para a variável *mês atual* e altere-o de volta para *hoje*.

<u>Resultados esperados</u>:

O gráfico de painel deve mostrar as estatísticas corretas o tempo todo.

<u>Resultados reais</u>:

O gráfico de painel mostra estatísticas incorretas na primeira carga. As estatísticas precisas do gráfico são atualizadas após o período.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

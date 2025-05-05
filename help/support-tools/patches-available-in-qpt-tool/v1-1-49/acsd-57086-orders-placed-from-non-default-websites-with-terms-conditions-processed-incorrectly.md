---
title: 'ACSD-57086: pedidos de sites não padrão com termos e condições ativados são processados incorretamente'
description: Aplique o patch ACSD-57086 para corrigir o problema do Adobe Commerce em que os pedidos feitos de sites não padrão com termos e condições ativados não são processados corretamente.
feature: Orders
role: Admin, Developer
exl-id: 400e3673-9c61-4acd-8e37-e9a2e0bf9379
source-git-commit: e61dd2874a2b6cb4c49aa6916c6273a2cb9f9e60
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# ACSD-57086: pedidos de sites não padrão com termos e condições ativados são processados incorretamente

O patch ACSD-57086 corrige o problema em que os pedidos feitos de sites não padrão com termos e condições ativados não são processados corretamente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 está instalado. A ID do patch é ACSD-57086. Observe que esse problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao usar uma configuração de várias lojas com processamento AsyncOrder, os pedidos feitos em qualquer site/loja que não seja o site principal são rejeitados devido a problemas com o manuseio de escopo no código de consumidor da fila.

<u>Etapas a serem reproduzidas</u>:

1. Instale [!DNL RabbitMQ] e execute `bin/magento setup:upgrade` para criar as filas para [!DNL RabbitMQ].
1. Configurar o processamento de AsyncOrder com:

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. Crie um site secundário, uma loja e uma visualização de loja.
1. Crie um produto que seja compartilhado entre os dois sites.
1. Ativar termos e condições:
   1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
   1. Defina *[!UICONTROL Enable Terms And Conditions]* como *Sim*.
1. Configure os termos e condições para ambos os sites:
   1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**.
   1. Use as seguintes configurações:
      * *[!UICONTROL Condition Name]*: *Qualquer Coisa*
      * *[!UICONTROL Status]*: *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*: *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*: *[!UICONTROL Default Store View]*
   1. Crie outra condição para a segunda exibição de site/loja.
1. Altere o site padrão indo para **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**. Clique no segundo site, marque *[!UICONTROL Set as Default]* e salve.
1. Limpar o cache com:

   ```bash
   bin/magento cache:clear
   ```

1. Acesse a Loja e adicione um produto ao carrinho. Prossiga para o check-out e faça um pedido (você deve ver uma caixa de seleção na etapa do método de pagamento para aceitar os termos e condições).
1. Volte para Admin depois de fazer o pedido, altere o site padrão de volta para o site principal original e salve.
1. Limpe o cache:

   ```bash
   bin/magento cache:clear
   ```

1. Execute o seguinte comando para iniciar o consumidor da fila:

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>Resultados esperados</u>:

A ordem é atendida; ela não é automaticamente rejeitada.

<u>Resultados reais</u>:

O status do pedido é *rejeitado* com o seguinte comentário:

*O pedido não foi feito. Primeiro, aceite os termos e condições e tente fazer seu pedido novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].

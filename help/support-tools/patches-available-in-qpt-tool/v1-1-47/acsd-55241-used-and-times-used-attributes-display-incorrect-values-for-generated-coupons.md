---
title: "ACSD-55241: **Used** e **Times Used** atributos exibem valores incorretos para cupons gerados"
description: Aplique o patch ACSD-55241 para corrigir o problema do Adobe Commerce em que os atributos **Usado** e **Horas usadas** exibem valores incorretos para cupons gerados
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241: **Usado** e **Vezes usado** os atributos exibem valores incorretos para cupons gerados

O patch ACSD-55241 corrige o problema em que o **Usado** e **Vezes usado** Os atributos do exibem valores incorretos para cupons gerados. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.47 está instalado. A ID do patch é ACSD-55241. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

**Usado** e **Vezes usado** Os atributos do exibem valores incorretos para cupons gerados.

<u>Etapas a serem reproduzidas</u>:

1. Criar **[!UICONTROL Cart Price Rules]** de **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** e adicione qualquer condição que corresponda ao fazer um pedido (Exemplo: subtotal maior que *5$*)

* Aplicar qualquer desconto.
* Selecionar **[!UICONTROL Auto Coupon]**.
* Ele gerará alguns códigos de cupom do **Gerenciar códigos de cupom**.
* Reindexe e limpe o cache.

1. Criar um **[!UICONTROL customer account]** e faça logon no front-end.
1. Adicionar um produto com mais de *2* quantidades no carrinho e aplique um cupom.
1. Clique em **[!UICONTROL Check Out with Multiple Addresses]**.
1. Selecione um endereço separado para cada quantidade, faça o pedido e conclua o processo de finalização.
1. Observe o total do pedido do administrador e veja o desconto aplicado.
1. Faça outro pedido com outro cupom.
1. Execute o `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` comando para atualizar o uso do código do cupom.

<u>Resultados esperados</u>:

A contagem correta deve ser exibida no **Tempo usado** e **Usado** colunas com **Sim** valor para **[!UICONTROL manage coupon]** no **[!UICONTROL cart price rule]** no admin.

<u>Resultados reais</u>:

A contagem de código de cupom usada não é atualizada no **Tempo usado** na grade de cupons, e a variável **Usado** mostra a *Não* se você colocar um pedido com vários endereços de entrega.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

---
title: '"ACSD-56635: os clientes importados são duplicados quando o compartilhamento de conta está definido como [!DNL Global]'''
description: Aplique o patch ACSD-56635 para corrigir o problema do Adobe Commerce em que o cliente importado é duplicado com o mesmo endereço de email quando a importação é usada com o compartilhamento de conta definido como [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
source-git-commit: 86d752c9c2791ef19960876afafe24fefe5d29ed
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635: os clientes importados são duplicados com o mesmo endereço de email quando o compartilhamento de conta é definido como [!DNL Global]

O patch ACSD-56635 corrige o problema em que o cliente importado é duplicado com o mesmo endereço de email quando a importação é usada com o compartilhamento de conta definido como [!DNL Global]. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.48 está instalado. A ID do patch é ACSD-56635. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes importados são duplicados com o mesmo endereço de email quando o compartilhamento de conta é definido como [!DNL Global].

<u>Etapas a serem reproduzidas</u>:

1. No Adobe Commerce (2.4-develop b2b) **[!UICONTROL Admin]**, acesso **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Defina o *[!UICONTROL Share Customer Accounts]* configuração para *[!DNL Global]*.
1. Criar vários sites e lojas:

   * ws1 > s11, s12 > sw111, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Crie um novo cliente sob o *site principal* do administrador com endereço de email usado como <adb@yormail.com>.
1. Em **[!UICONTROL Admin]**, navegue até **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Selecionar **[!UICONTROL Customer Entity Type]** as *[!UICONTROL Customers Main File]*.
1. Usar o mesmo endereço de email que <adb@yormail.com> em um site diferente, por exemplo, ws1. Consulte o arquivo CSV de exemplo customer.csv fornecido abaixo.
1. Conclua a importação para ver o novo usuário criado na *ws1* site com o mesmo endereço de email.

conteúdo do customer.csv:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Resultados esperados</u>:

O cliente importado com o mesmo endereço de email é atualizado em vez de ser duplicado.

<u>Resultados Reais</u>:

Clientes duplicados são criados com o mesmo endereço de email ao usar a importação do cliente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

---
title: '"ACSD-55112: [!UICONTROL Sumbit Review] pode ser clicado várias vezes'''
description: Aplique o patch ACSD-55112 para corrigir o problema do Adobe Commerce em que o [!UICONTROL Submit Review] pode ser clicado várias vezes sem [!DNL Google reCAPTCHA v3] validação.
feature: Products
role: Admin, Developer
exl-id: db202472-1d96-4ac0-8ecd-eab84c9f4cbf
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# ACSD-55112: o [!UICONTROL Submit Review] pode ser clicado várias vezes

>[!NOTE]
>
>Este patch substitui o [ACSD-51890](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51890-submit-review-button-can-be-clicked-multiple-times.md).

O patch ACSD-55112 corrige o problema em que o [!UICONTROL Submit Review] pode ser clicado várias vezes sem [!DNL Google reCAPTCHA v3] validação. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.42 está instalado. A ID do patch é ACSD-55112. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorrendo o seguinte erro:

```JS
_jquery.validate.js:799 Uncaught TypeError: Cannot read properties of undefined (reading 'call'). Exception occurred when checking element login-email, check the 'validate' method.
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

---
title: '"ACSD-51890: [!UICONTROL Submit review] pode ser clicado várias vezes'''
description: Aplique o patch ACSD-51890 para corrigir o problema do Adobe Commerce em que o [!UICONTROL Submit Review] pode ser clicado várias vezes sem [!DNL Google reCAPTCHA v3] validação.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890: **[!UICONTROL Submit Review]** pode ser clicado várias vezes sem **[!DNL Google reCAPTCHA v3]** validação

>[!NOTE]
>
>Este patch foi substituído por [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

O patch ACSD-51890 corrige o problema em que a variável **[!UICONTROL Submit Review]** pode ser clicado várias vezes sem **[!DNL Google reCAPTCHA v3]** validação. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.35 está instalado. A ID do patch é ACSD-51890. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A variável **[!UICONTROL Submit Review]** pode ser clicado várias vezes sem a opção **[!DNL Google reCAPTCHA v3]** validação.

<u>Etapas a serem reproduzidas</u>:

1. Ativar **[!DNL Google reCAPTCHA v3]** para a revisão do produto.
1. Abra a página do produto e navegue até o **[!UICONTROL Review]** e verifique se o [!DNL reCAPTCHA] está visível.
1. Preencha o formulário de revisão e clique em **[!UICONTROL Submit Review]** várias vezes o mais rápido possível.
1. Abra o **[!UICONTROL Review]** do Administrador.

<u>Resultados esperados</u>

Revisões duplicadas não são criadas.

<u>Resultados reais</u>

Revisões duplicadas são criadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no [!DNL Quality Patches Tool] guia.

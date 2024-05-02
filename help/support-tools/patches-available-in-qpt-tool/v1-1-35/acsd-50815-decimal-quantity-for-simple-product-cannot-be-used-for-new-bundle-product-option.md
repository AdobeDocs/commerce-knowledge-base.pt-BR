---
title: "ACSD-50815: a quantidade decimal do produto simples não pode ser usada para a nova opção de produto agrupada"
description: Aplique o patch ACSD-50815 para corrigir o problema do Adobe Commerce em que a quantidade decimal de um produto simples não pode ser usada para uma nova opção de produto agrupado.
feature: Products
role: Admin
exl-id: f4aa417c-b0eb-4a68-bf1e-fd86770cc72d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-50815: a quantidade decimal do produto simples não pode ser usada para a opção de novo produto agrupado

O patch ACSD-50815 corrige o problema em que a quantidade decimal de um produto simples não pode ser usada para uma nova opção de produto agrupado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.35 está instalado. A ID do patch é ACSD-50815. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A quantidade decimal de um produto simples não pode ser usada para uma nova opção de produto agrupada.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como administrador.
1. Crie um novo produto simples.
   * No **[!UICONTROL Advanced Inventory]** janela, definir [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes].
   * Salve o produto simples.
1. Crie um novo produto incluído.
1. Adicione qualquer opção.
1. Adicione o produto simples nesta opção.
1. Defina uma quantidade decimal para o produto simples na opção de produto agrupado. Por exemplo, 1.5.

<u>Resultados esperados</u>:

É possível definir a quantidade decimal. Nenhum erro é exibido.

<u>Resultados reais</u>:

O erro, *Insira um número válido neste campo* é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

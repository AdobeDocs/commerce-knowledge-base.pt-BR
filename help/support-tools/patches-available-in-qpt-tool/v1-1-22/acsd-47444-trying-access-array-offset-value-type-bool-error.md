---
title: '"ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_ erro ao acessar certos caminhos de categorias não existentes para produtos conhecidos no PHP 7.4'''
description: Aplique o patch ACSD-47444 para corrigir o problema do Adobe Commerce em que há um _[!UICONTROL Trying to access array offset on value of type bool]_ erro ao acessar certos caminhos de categorias não existentes para produtos conhecidos, no PHP 7.4.
exl-id: dfe803d0-bcff-40e6-a759-8c2243235ea8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_erro ao acessar certos caminhos de categorias não existentes para produtos conhecidos no PHP 7.4

O patch ACSD-47444 resolve o problema em que você vê _[!UICONTROL Trying to access array offset on value of type bool]_erro ao acessar certos caminhos de categorias não existentes para produtos conhecidos no PHP 7.4. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.22 está instalado.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorreu o seguinte erro: _[!UICONTROL Trying to access array offset on value of type bool]_no PHP 7.4, quando você acessa caminhos de categorias não existentes para produtos conhecidos.

<u>Pré-requisitos</u>:

PHP 7.4.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo produto - com o nome &quot;test&quot;.
1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > definir **[!UICONTROL Generate "category/product" URL Rewrites]** = _Não_.
1. Acesse a loja e visite o URL como ../abc/test.html (&quot;abc&quot; - não deveria existir).

<u>Resultados esperados</u>:

página 404.

<u>Resultados reais</u>:

Erro 500:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

---
title: "ACSD-54106: Retificação da classificação de caracteres acentuados turcos na categoria do produto"
description: Aplique o patch ACSD-54106 para corrigir o problema do Adobe Commerce em que a classificação de produto de categoria por nome para caracteres com acento turco está incorreta.
feature: Categories, Products, Search
role: Admin
exl-id: 80386ded-4ada-4822-b073-f477ca123093
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-54106: Retificação da classificação de caracteres acentuados turcos na categoria de produto

O patch ACSD-54106 corrige o problema em que a classificação de produto de categoria por nome para caracteres acentuados turcos está incorreta. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.39 está instalado. A ID do patch é ACSD-54106. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A classificação de produtos em categorias por nome está incorreta para caracteres com acento turco.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no painel de administração.
1. Crie produtos simples nomeados da seguinte maneira e atribua-os a qualquer categoria:

* Nome A
* Nome Ç
* Nome D
* Nome ➡
* Nome M
* Nome Ö
* Nome Ü
* Nome Y
* Nome Z

1. Navegue até a loja e acesse a categoria que contém os produtos.
1. Modifique a ordem de classificação para *[!UICONTROL By Name]*.

<u>Resultados esperados</u>:

Os produtos são classificados corretamente na seguinte ordem:

* Nome A
* Nome Ç
* Nome D
* Nome ➡
* Nome M
* Nome Ö
* Nome Ü
* Nome Y
* Nome Z

<u>Resultados reais</u>:

Os produtos são classificados incorretamente na seguinte ordem:

* Nome A
* Nome D
* Nome M
* Nome Y
* Nome Z
* Nome Ç
* Nome Ö
* Nome Ü
* Nome ➡

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

---
title: '"ACSD-59280: erro "RefletionUnionType::getName()" em instalações 2.4.4-pX"'
description: Aplique o patch ACSD-59280 para corrigir o problema do Adobe Commerce em que o erro "call to undefined method RefletionUnionType::getName()" ocorre durante a instalação das versões 2.4.4-pX.
feature: Install, Upgrade
role: Admin, Developer
source-git-commit: a7a42520c6c7d74e995d104271afa2b15b537de7
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-59280: erro `ReflectionUnionType::getName()` em instalações 2.4.4-pX

O patch ACSD-59280 corrige o problema em que o erro `call to undefined method ReflectionUnionType::getName()` ocorre durante a instalação das versões 2.4.4-pX. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 está instalado. A ID do patch é ACSD-59280. Observe que o problema foi corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro `ReflectionUnionType::getName()` durante a instalação do 2.4.4-pX.

<u>Etapas a serem reproduzidas</u>:

Executar uma nova instalação usando o *[!UICONTROL Composer]*.

<u>Resultados esperados</u>:

O processo de instalação é concluído sem erros.

<u>Resultados reais</u>:

Você vê o seguinte erro durante o processo `setup:upgrade`:

`Call to undefined method ReflectionUnionType::getName()`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
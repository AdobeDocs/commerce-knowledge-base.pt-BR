---
title: 'ACSD-48204: a regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado'
description: Aplique o patch ACSD-48204 para corrigir o problema do Adobe Commerce em que a regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado.
exl-id: 9b0b4d62-c4c5-40d7-a279-52f59ee7ac42
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-48204: a regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado

O patch ACSD-48204 corrige o problema em que a regra de preço do catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 está instalado. A ID do patch é ACSD-48204. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois sites (Padrão e W2).
1. Crie um atributo de produto do tipo *Sim/Não*.
   * Conjunto [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Crie um produto configurável com base em qualquer atributo com duas variações (V1 e V2).
   * Adicionar o atributo *Sim/Não* ao conjunto de atributos de variações configuráveis
   * Para uma das variações (V1), defina o valor como *[!UICONTROL Yes]* no site não padrão (W2)
1. Criar uma regra de catálogo:
   * Aplicado a ambos os sites
   * Condição: *Sim/Não* o valor do atributo é *[!UICONTROL Yes]*
   * Desconto = 50%
1. Abra o produto configurável no site fora do padrão (W2).
1. Verifique se a variação V1 tem o desconto de 50% aplicado.
1. Abra a variação V1 no Administrador do Adobe Commerce.
   * Alternar para o site padrão
   * Não fazer alterações e salvar o produto
1. Atualize a página inicial da loja de produtos configurável.

<u>Resultados esperados</u>:

A variação V1 ainda tem o desconto de 50% aplicado, pois nenhuma alteração foi feita.

<u>Resultados reais</u>:

O desconto desaparece.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].

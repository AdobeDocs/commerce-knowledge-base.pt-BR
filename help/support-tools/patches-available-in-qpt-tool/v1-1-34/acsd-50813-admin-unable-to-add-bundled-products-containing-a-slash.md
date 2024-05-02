---
title: "ACSD-50813: o administrador não pode adicionar produtos empacotados que contenham uma barra"
description: Aplique o patch ACSD-50813 para corrigir o problema de desempenho do Adobe Commerce em que o administrador não pode adicionar produtos empacotados contendo uma marca de barra (`/`) no SKU com a funcionalidade *Adicionar produtos por SKU* à ordem do administrador.
exl-id: 80dfe877-9dfd-44a9-9bf0-37e929642fc0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-50813: O administrador não pode adicionar produtos empacotados que contenham uma barra

O patch ACSD-50813 corrige o problema em que o administrador não pode adicionar produtos empacotados que contenham uma marca de barra (`/`) no SKU com o *[!UICONTROL Add Products by SKU]* para a ordem do administrador. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.34 está instalado. A ID do patch é ACSD-50813. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O administrador não pode adicionar produtos agrupados que contenham uma marca de barra (`/`) no SKU com o *[!UICONTROL Add Products by SKU]* para a ordem do administrador.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Crie um produto simples.
1. Crie um novo produto incluído.
1. Adição de uma marca de barra (`/`) no meio do SKU (Exemplo: *Bu/ndle*).
1. Adicionar uma opção agrupada com **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*.
1. Atribua pelo menos um produto simples à opção.
1. Ir para **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e criar um novo pedido.
1. Clique em **[!UICONTROL Add Products by SKU]**.
1. Insira seu SKU e clique em **[!UICONTROL Add to Order]**.
1. Abra o console do navegador.
1. Clique em **[!UICONTROL Configure]**.

<u>Resultados esperados</u>:

Não há erros.

<u>Resultados reais</u>:

Erro JS no console:

*Erro não detectado: Erro de sintaxe, expressão não reconhecida: div[id=sku_bu/ndle]*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

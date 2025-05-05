---
title: 'ACSD-51645: Salvando uma nova Regra de preço do carrinho se a extensão Magento_OfflineShipping estiver desativada'
description: Aplique o patch ACSD-51645 para corrigir o problema do Adobe Commerce em que ocorre um erro ao salvar uma nova Regra de preço do carrinho se a extensão Magento_OfflineShipping estiver desativada.
exl-id: 301086bb-7aab-4e74-93e6-9080eebcb026
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-51645: Salvando uma nova Regra de preço do carrinho se a extensão Magento_OfflineShipping estiver desativada

O patch ACSD-51645 corrige o problema em que ocorre um erro ao salvar uma nova Regra de preço do carrinho se a extensão Magento_OfflineShipping estiver desativada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. A ID do patch é ACSD-51645. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR>). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro ao salvar uma nova Regra de Preço do Carrinho se a extensão `Magento_OfflineShipping` estiver desabilitada.

<u>Etapas a serem reproduzidas</u>:

1. Desabilite o módulo `Magento_OfflineShipping`.
1. Faça logon em **Admin**.
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. Criar um novo **[!UICONTROL Cart Price Rule]**.
1. Preencha os campos obrigatórios.
1. Salve o **[!UICONTROL Cart Price Rule]**.

<u>Resultados esperados</u>:

A regra de preço do carrinho foi salva com sucesso.

<u>Resultados reais</u>:

Ocorre o seguinte erro:
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR>) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR>) no guia [!DNL Quality Patches Tool].

---
title: "ACSD-49480: descartar regras subsequentes que não estejam funcionando"
description: Aplique o patch ACSD-49480 para corrigir o problema do Adobe Commerce em que o [!UICONTROL Cart Price Rule - Discard Subsequent Rules] não está funcionando como esperado.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] não está funcionando como pretendido

O patch ACSD-49480 corrige o problema em que a variável [!UICONTROL Cart Price Rule - Discard Subsequent Rules] não está funcionando como esperado. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.32 está instalado. A ID do patch é ACSD-49480. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] não está funcionando como esperado.

<u>Etapas a serem reproduzidas</u>:

1. Criar um **[!UICONTROL Cart Price Rule]** com um código de cupom (nomeie-o como *TESTE*) que oferece um desconto de US$ 10 para o *ID do produto 1* no **[!UICONTROL Actions]** guia com [!UICONTROL Discard Subsequent Rules] definir como *[!UICONTROL Yes]* e [!UICONTROL Priority] definir como *1*.
1. Criar outro **[!UICONTROL Cart Price Rule]** sem um código de cupom que dê um desconto de US$ 5 para *ID do produto 2* no **[!UICONTROL Actions]** guia com [!UICONTROL Priority] definir como *2*. Aqui, assumimos, esta é uma venda global para *ID do produto 2*.
1. Ir para o site de front-end e adicionar *ID do produto 1* e *ID do produto 2* no carrinho.
1. Aplique o *TESTE* código do cupom.

<u>Resultados esperados</u>

* *Desconto 1* é aplicado a *ID do produto 1*.
* *Desconto 2* é aplicado a *ID do produto 2*.

<u>Resultados reais</u>

* Somente *Desconto 1* é aplicado a *ID do produto 1*.
* *Desconto 2* não é aplicado a *ID do produto 2*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

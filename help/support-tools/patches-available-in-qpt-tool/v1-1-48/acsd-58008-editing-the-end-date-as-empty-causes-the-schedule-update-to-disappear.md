---
title: 'ACSD-58008: editar a data de término como *empty* faz com que a atualização da programação desapareça'
description: Aplique o patch ACSD-58008 para corrigir o problema do Adobe Commerce em que editar a data de término como *vazia* faz com que a atualização de agendamento desapareça.
feature: Staging, Page Content
role: Admin, Developer
source-git-commit: 174ed3b35edeb26b09b04bc7d88111a5719e08f8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: Edição da data final como *vazio* faz com que a atualização da programação desapareça

O patch ACSD-58008 corrige o problema em que editar a data final como *vazio* faz com que a atualização do cronograma desapareça. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.48 está instalado. A ID do patch é ACSD-58008. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Editar a data final como *vazio* faz com que a atualização da programação desapareça

<u>Etapas a serem reproduzidas</u>:

1. Fazer logon como [!UICONTROL Admin].
1. Ir para **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** e crie uma página.
1. Selecione a página criada e clique em **[!UICONTROL Schedule New Update]**. *(Navegue até o canto superior direito da página)*.
1. Crie quatro atualizações. *(Por exemplo, como um incremento de* 2 *minutos)*.
1. Atualize o *atualização 2* e altere o horário para um horário que esteja à frente do último *atualização 4*.
1. Salve as atualizações feitas.

<u>Resultados esperados</u>:

A atualização da programação mostra a *atualização 3*.

<u>Resultados reais</u>:

A atualização da programação não mostra a *atualização 3*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
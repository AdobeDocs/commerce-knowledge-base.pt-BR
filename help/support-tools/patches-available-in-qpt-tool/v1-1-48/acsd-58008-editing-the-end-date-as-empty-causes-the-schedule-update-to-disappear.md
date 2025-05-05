---
title: 'ACSD-58008: editar a data final como *vazia* faz com que a atualização da programação desapareça'
description: Aplique o patch ACSD-58008 para corrigir o problema do Adobe Commerce em que editar a data de término como *vazia* faz com que a atualização de agendamento desapareça.
feature: Staging, Page Content
role: Admin, Developer
exl-id: bfa590b8-377b-49dd-9aff-f89b8fd815c4
source-git-commit: d7ace1f20defb01105d4a241f971b06fca052215
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: Editar a data final como *vazia* faz com que a atualização da programação desapareça

O patch ACSD-58008 corrige o problema em que editar a data de término como *vazia* faz com que a atualização de agendamento desapareça. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 está instalado. A ID do patch é ACSD-58008. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Editar a data de término como *vazia* faz com que a atualização da agenda desapareça

<u>Etapas a serem reproduzidas</u>:

1. Fazer logon como [!UICONTROL Admin].
1. Vá para **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** e crie uma página.
1. Selecione a página criada e clique em **[!UICONTROL Schedule New Update]**. *(Navegue até o canto superior direito da página)*.
1. Crie quatro atualizações. *(Por exemplo, como um incremento de* 2 *minutos)*.
1. Atualize a *atualização 2* e altere o horário para um horário que esteja à frente da última *atualização 4*.
1. Salve as atualizações feitas.

<u>Resultados esperados</u>:

A atualização da agenda mostra a *atualização 3*.

<u>Resultados reais</u>:

A atualização da agenda não mostra a *atualização 3*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].

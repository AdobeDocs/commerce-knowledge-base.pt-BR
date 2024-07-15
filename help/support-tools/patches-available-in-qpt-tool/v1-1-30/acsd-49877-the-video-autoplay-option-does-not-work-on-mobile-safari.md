---
title: "ACSD-49877: a reprodução automática de vídeo não funciona no celular [!DNL Safari]"
description: Aplique o patch ACSD-49877 para corrigir o problema do Adobe Commerce em que a opção de reprodução automática de vídeo não funciona em dispositivos móveis [!DNL Safari] quando o vídeo estiver vinculado diretamente a um arquivo de vídeo remoto.
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877: a reprodução automática de vídeo não funciona no [!DNL Safari] móvel

O ACSD-49877 corrige o problema em que a opção de reprodução automática no [!DNL Safari] móvel não funciona quando o vídeo é vinculado diretamente a um arquivo de vídeo remoto. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. A ID do patch é ACSD-49877. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote [!magento/quality-patches] para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Pesquisar patches]. Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A reprodução automática de vídeo não funciona no [!DNL Safari] móvel quando o vídeo é vinculado diretamente a um arquivo de vídeo remoto e não a um serviço de streaming.

<u>Pré-requisitos</u>:
[!DNL Page Builder] módulos estão instalados.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova página CMS e edite o **[!UICONTROL Content Value]** com [!DNL Page Builder].
1. Adicione um elemento *Tab* ao conteúdo e adicione um *Elemento de Vídeo* dentro da *Tab*.
1. Agora clique no botão de engrenagem para editar o *Elemento de vídeo*.
1. Adicione um link para um arquivo de vídeo mp4 ao campo [!UICONTROL Video URL].
1. Marcar o campo **[!UICONTROL Autoplay]** como *Sim*.
1. Clique em **[!UICONTROL Save]**.
1. Abra a página criada recentemente em [!DNL Safari] usando uma iPhone.

<u>Resultados esperados</u>

A opção de reprodução automática funciona em [!DNL Safari] usando uma iPhone.

<u>Resultados reais</u>

A opção de reprodução automática não funciona em [!DNL Safari] usando uma iPhone.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

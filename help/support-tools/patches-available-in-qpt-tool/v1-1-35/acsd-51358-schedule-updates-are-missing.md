---
title: "ACSD-51358: atualizações de programação estão ausentes"
description: Aplique o patch ACSD-51358 para corrigir o problema do Adobe Commerce em que as alterações na atualização agendada sem uma data final levam à remoção de outras atualizações agendadas na mesma entidade.
feature: Staging
role: Admin, Developer
exl-id: 8bc4c505-9cf2-4c33-93a1-4b4d7d0dfc15
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51358: atualizações de programação ausentes

O patch ACSD-51358 corrige o problema em que as alterações na atualização agendada sem uma data final levam à remoção de outras atualizações agendadas na mesma entidade. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.35 está instalado. A ID do patch é ACSD-51358. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As alterações na atualização agendada sem uma data de término levam à remoção de outras atualizações agendadas na mesma entidade.

<u>Etapas a serem reproduzidas</u>:

1. Criar um **[!UICONTROL scheduled update]** sem a data final (*atualização 1*).
1. Criar novo **[!UICONTROL scheduled update]** com a mesma data inicial da primeira atualização, mas adicione o dia seguinte e a data final (*atualização 2*).
1. Editar **[!UICONTROL scheduled update]** criado na etapa 1 (*atualização 1*) e salve as alterações.

<u>Resultados esperados</u>

O (*atualização 2*) devem permanecer no **[!UICONTROL schedule update]** listar quando (*atualização 1*) é editado.

<u>Resultados reais</u>

O (*atualização 2*) foi removido do **[!UICONTROL schedule update]** listar quando (*atualização 1*) é editado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no [!DNL Quality Patches Tool] guia.

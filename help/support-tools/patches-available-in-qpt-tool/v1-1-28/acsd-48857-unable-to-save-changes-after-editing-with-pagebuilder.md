---
title: '"ACSD-48857: não é possível salvar as alterações após a edição com [!DNL Page Builder]'''
description: Aplique o patch ACSD-48857 para corrigir o problema do Adobe Commerce em que o usuário não pode salvar alterações após editar com [!DNL Page Builder].
exl-id: c95b354d-8954-4e9c-9e92-8a64f62f0a68
feature: Admin Workspace, CMS, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-48857: não é possível salvar as alterações após a edição com [!DNL Page Builder]

O patch ACSD-48857 corrige o problema em que o usuário não consegue salvar alterações após editar com [!DNL Page Builder]. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.28 está instalado. A ID do patch é ACSD-48857. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário não pode salvar as alterações após editar com [!DNL Page Builder].

<u>Etapas a serem reproduzidas</u>

1. Faça logon no site de administração.
1. Navegue até **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** para criar uma página CMS vazia.
1. Execute este script SQL para definir o seguinte **[!UICONTROL Content]** valor do campo:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Retornar para **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** em Admin.
1. Edite sua página.
1. Vá para a **[!UICONTROL Content]** guia.
1. Clique em **[!UICONTROL Save]**.

<u>Resultados esperados</u>

A limpeza de conteúdo HTML é implementada. Isso remove [!DNL Page Builder] atributos HTML reservados em conteúdos gerados pelo editor de texto.

<u>Resultados reais</u>

A página permanece não salva e o carregador continua girando. No console, o seguinte erro é gerado:

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

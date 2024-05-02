---
title: "ACSD-53414: os usuários administradores restritos podem ver páginas do CMS fora do escopo de permissões"
description: Aplique o patch ACSD-53414 para corrigir o problema do Adobe Commerce em que um usuário administrador restrito pode ver páginas CMS fora do escopo de permissões.
feature: CMS
role: Admin, Developer
exl-id: f8540d52-a3bb-49bb-8868-7b1db03e571b
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53414: Os usuários administradores restritos podem ver páginas do CMS fora do escopo de permissões

O patch ACSD-53414 corrige o problema em que um usuário administrador restrito pode ver páginas do CMS fora do escopo de permissões. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.40 está instalado. A ID do patch é ACSD-53414. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários administradores restritos podem ver as páginas do CMS além do escopo de permissões.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo site (sub_website), loja (sub_store) e loja (sub_storeview).
1. Crie uma função sub_expert, permitindo o escopo de sub_website e sub_store. Atribuir somente as seguintes permissões: [!UICONTROL Dashboard] e [!UICONTROL Pages].
1. Crie um novo usuário administrador e atribua-o à função sub_expert.
1. Atribua as seguintes páginas CSM a sub_storeview e storeview padrão.

   * [!UICONTROL 404 Not Found] > Sub-loja
   * [!UICONTROL 503 Service Unavailable] > Loja padrão

1. Faça logon no Administrador usando o usuário administrador criado na Etapa 3.
1. Verifique a grade da página do CMS.

<u>Resultados esperados</u>:

*[!UICONTROL 503 Service Unavailable]* não está visível para o administrador da web.

<u>Resultados reais</u>:

*[!UICONTROL 503 Service Unavailable]* está visível para o administrador da web.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

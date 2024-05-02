---
title: "ACSD-57337: o usuário administrador com restrições de acesso pode visualizar todas as empresas na grade *Empresas*"
description: Aplique o patch ACSD-57337 para corrigir o problema do Adobe Commerce em que um usuário administrador com restrições de acesso a sites específicos pode visualizar empresas de todos os sites na grade *Empresas*.
feature: Companies, B2B, Configuration
role: Admin, Developer
source-git-commit: a02c80006f1c8a434fe17322f0c6cee25f086396
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-57337: O usuário administrador com restrições de acesso pode visualizar todas as empresas no *Empresas* grade

O patch ACSD-57337 corrige o problema em que um usuário administrador com restrições de acesso a sites específicos pode visualizar empresas de todos os sites na *Empresas* grade. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.48 está instalado. A ID do patch é ACSD-57337. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um usuário administrador com restrições de acesso a sites específicos pode exibir empresas de todos os sites na *Empresas* grade.

<u>Etapas a serem reproduzidas</u>:

1. Crie um site, uma loja e uma loja adicionais.
1. Crie algumas empresas atribuídas a sites diferentes.
1. Crie uma função de usuário administrador e defina o escopo da função para o site criado.
1. Crie um administrador e atribua-o à função criada.
1. Faça logon com um novo administrador.
1. Abertura **[!UICONTROL Customers]** > **[!UICONTROL Companies]** e observe a lista de empresas.

<u>Resultados esperados</u>:

As empresas que foram atribuídas ao site adicional estão visíveis na *Empresas* grade.

<u>Resultados reais</u>:

Todas as empresas estão visíveis na *Empresas* grade.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
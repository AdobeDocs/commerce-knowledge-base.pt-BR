---
title: "MDVA-34867: valores do conjunto de campos de condição para Atualização agendada não salvos"
description: O patch MDVA-34867 resolve o problema em que o valor da condição na nova atualização de agendamento não é salvo ao editar uma regra de preço de catálogo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: bf514ccc-bebd-4ed2-868f-28b02b1e253e
feature: Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-34867: valores do conjunto de campos de condição para Atualização agendada não salvos

O patch MDVA-34867 resolve o problema em que o valor da condição na nova atualização de agendamento não é salvo ao editar uma regra de preço de catálogo. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.17 está instalado. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.0-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O valor da condição na nova atualização de agendamento não está sendo salvo ao editar uma regra de preço de catálogo.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Admin.
1. Criar um **Regra de catálogo** com **Condição** = &quot;*A categoria é 1*&quot;.
1. Agendar uma atualização com uma data de início no futuro (Exemplo: amanhã) e definir **Condição** = &quot;*A categoria é 2, 3*&quot; e salve a atualização.
1. Clique em **Exibir/Editar** para a atualização criada acima, e verifique os campos de condição.

<u>Resultados esperados</u>:

A variável **da regra do catálogo**  **Condição** = &quot;*A categoria é 2, 3*&quot;, conforme esperado.

<u>Resultados reais</u>:

A variável **da regra do catálogo**  **Condição** = &quot;*A categoria é 1*&quot;, o que significa que a atualização não foi salva.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.

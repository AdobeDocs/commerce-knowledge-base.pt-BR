---
title: "ACSD-52219: Resolução de um problema de filtro de grades do administrador na alternância da exibição de marcador"
description: Aplique o patch ACSD-52219 para corrigir o problema do Adobe Commerce em que os filtros salvos das grades de administrador não funcionam como esperado ao alternar frequentemente entre exibições de marcadores.
feature: Admin Workspace
role: Admin
exl-id: e8333ee7-28a8-4457-aeff-6828f8ca9412
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52219: Resolução de um problema de filtro de grades de administrador na alternância da exibição de marcador

O patch ACSD-52219 corrige o problema em que os filtros salvos das grades de administrador não funcionam como esperado ao alternar frequentemente entre exibições de marcadores. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.39 está instalado. A ID do patch é ACSD-52219. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao alternar frequentemente entre exibições de marcadores, os filtros salvos nas grades de administração não funcionam como esperado.

<u>Etapas a serem reproduzidas</u>:

1. Acesse o [!DNL Sales Order] no Admin.
1. Crie dois a três filtros.
1. Verifique as configurações de filtro alternando as exibições para garantir que elas sejam salvas com precisão.
1. Vá para Filtro1 ou Filtro2.
1. Atualize a página para atualizar os dados exibidos.
1. Alterne para uma exibição diferente e observe que os filtros permanecem inalterados.
1. Observe que a exibição padrão agora exibe os resultados filtrados, mesmo que nenhum filtro específico tenha sido definido para ela.

<u>Resultados esperados</u>:

Os filtros não são trocados e mantêm seu estado original.

<u>Resultados reais</u>:

Ao modificar uma exibição, os filtros são misturados e a exibição correta não é salva.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.

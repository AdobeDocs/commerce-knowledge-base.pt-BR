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

O patch ACSD-52219 corrige o problema em que os filtros salvos das grades de administrador não funcionam como esperado ao alternar frequentemente entre exibições de marcadores. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 está instalado. A ID do patch é ACSD-52219. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao alternar frequentemente entre exibições de marcadores, os filtros salvos nas grades de administração não funcionam como esperado.

<u>Etapas a serem reproduzidas</u>:

1. Acesse a grade [!DNL Sales Order] no Administrador.
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

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

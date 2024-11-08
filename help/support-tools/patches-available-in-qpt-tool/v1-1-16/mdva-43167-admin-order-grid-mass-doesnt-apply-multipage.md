---
title: "MDVA-43167: a ação em massa da grade de ordem do administrador não se aplica a páginas múltiplas"
description: O patch MDVA-43167 corrige o problema em que a ação em massa da grade de ordem do administrador não se aplica a várias páginas quando o usuário administrador seleciona todos os pedidos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 está instalada. A ID do patch é MDVA-43167. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 58a126db-8a4f-4e20-8fe5-3ce2e25edf7e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# MDVA-43167: a ação em massa da grade de ordem do administrador não se aplica a páginas múltiplas

O patch MDVA-43167 corrige o problema em que a ação em massa da grade de ordem do administrador não se aplica a várias páginas quando o usuário administrador seleciona todos os pedidos. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 está instalada. A ID do patch é MDVA-43167. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A ação em massa da grade de ordem do administrador não se aplica a várias páginas quando o usuário administrador seleciona todos os pedidos.

<u>Etapas a serem reproduzidas</u>:

1. Compre qualquer produto três vezes para criar três pedidos.
1. Navegue até **Grade de Ordens de Venda**.
1. Altere a paginação para um valor personalizado de 2.
1. Selecionar tudo.
1. Selecione **Reter Ação em Massa**.

<u>Resultados esperados</u>:

Todos os três pedidos são colocados em espera.

<u>Resultados reais</u>:

Somente as duas ordens visíveis são colocadas em retenção.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.

---
title: "MDVA-32449: histórico de ordens de venda lento ou não carrega com erro 503"
description: O patch MDVA-32449 resolve o problema no Adobe Commerce em que o histórico de ordens de venda carrega lentamente ou não carrega e exibe um erro 503. Esse é um problema quando mais de 13000 clientes são atribuídos a uma empresa B2B. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalada. Observe que esse problema foi corrigido no Adobe Commerce 2.4.1.
exl-id: e3fd4db2-b706-4712-ba8e-270eaca7fdb2
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-32449: histórico de ordens de venda lento ou não carrega com erro 503

O patch MDVA-32449 resolve o problema no Adobe Commerce em que o histórico de ordens de venda carrega lentamente ou não carrega e exibe um erro 503. Esse é um problema quando mais de 13000 clientes são atribuídos a uma empresa B2B. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalada. Observe que esse problema foi corrigido no Adobe Commerce 2.4.1.

## Produtos e versões afetados

Esse é um problema quando mais de 13000 clientes são atribuídos a uma empresa B2B.

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige o problema em que o histórico do pedido é carregado muito lentamente ou não é carregado.

<u>Pré-requisitos</u>:

Mais de 13000 clientes atribuídos a uma empresa B2B

<u>Etapas a serem reproduzidas</u>:

1. Faça logon na loja como o administrador da empresa.
1. Ir para a página de histórico de ordens de venda.

<u>Resultados esperados</u>:

A página de histórico das ordens de venda é carregada normalmente.

<u>Resultados reais</u>:

A página é carregada muito lentamente ou talvez não seja carregada e um erro de tempo limite é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

---
title: "MDVA-34680: conta do cliente não filtrada corretamente na grade dos clientes"
description: O patch MDVA-34680 corrige o problema quando a conta do cliente criada após as 00:00 UTC não é filtrada corretamente na grade do cliente. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 está instalada. A ID do patch é MDVA-34680. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 2e506d7a-8cde-41eb-84b2-1a5ff8015428
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-34680: Conta do cliente não filtrada corretamente na grade dos clientes

O patch MDVA-34680 corrige o problema quando a conta do cliente criada após as 00:00 UTC não é filtrada corretamente na grade do cliente. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 está instalada. A ID do patch é MDVA-34680. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.1 e 2.4.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.6-2.3.7 e 2.4.1-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando uma conta de cliente é criada depois das 00:00 UTC e você tenta filtrar as contas até essa data, ela não retorna esse cliente.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Lojas** > **Configuração** > **Geral** e defina o Fuso Horário como Padrão do Leste [Estados Unidos/Nova York].
1. Crie uma nova conta de cliente depois das 00:00 UTC.
1. Vá para **Clientes** > **Todos os Clientes** e filtre as contas pela data de hoje.

<u>Resultados esperados</u>:

Os filtros de conta do cliente mostram a nova conta criada hoje após as 00:00 UTC.

<u>Resultados reais</u>:

Os filtros de conta do cliente não mostram a nova conta criada hoje.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

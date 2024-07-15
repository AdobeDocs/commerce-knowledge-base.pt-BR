---
title: "Patch MDVA-32759: catálogos compartilhados excluem preços de camada"
description: O patch MDVA-32759 resolve o problema em que os catálogos compartilhados excluem os preços de camada existentes.
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Patch MDVA-32759: catálogos compartilhados excluem preços de camada

O patch MDVA-32759 resolve o problema em que os catálogos compartilhados excluem os preços de camada existentes.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisitos</u>:

Instale o Adobe Commerce com B2B, com **Recursos B2B** habilitados.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Lojas > Configuração > Recursos B2B > Habilitar Empresa** e **Catálogo Compartilhado**.
1. Executar `bin/magento cron:run`.
1. Crie um produto simples, clique em **Preços avançados**, adicione **Preço do catálogo e da camada** e salve-o.
1. Vá para **Catálogo > Catálogo Compartilhado > Definir Preço e Estrutura**, clique em **Configurar** e, nesse menu suspenso, desmarque todas as opções e salve.
1. Executar `bin/magento cron:run`.
1. Abra o produto criado acima e verifique o Advanced Pricing.

<u>Resultados esperados</u>:

Os preços de nível não devem ser removidos dos produtos após a remoção de todos os produtos do catálogo público compartilhado, conforme esperado.

<u>Resultados reais</u>:

Os preços da camada são removidos após a remoção de todos os produtos do catálogo público compartilhado.


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

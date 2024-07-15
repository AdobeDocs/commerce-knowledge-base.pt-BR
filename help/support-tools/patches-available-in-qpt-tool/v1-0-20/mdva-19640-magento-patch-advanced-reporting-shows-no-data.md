---
title: "MDVA-19640: relatórios avançados não mostram dados"
description: O patch MDVA-19640 corrige o problema quando os Relatórios avançados não mostram dados. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-19640. Observe que não há nenhum plano atual para corrigir esse problema em versões futuras.
exl-id: 6df70f10-5d34-4540-b2ae-3a0be32f2bfd
feature: Commerce Intelligence
role: Admin
source-git-commit: 2914a110444898f78d2ed43ea96a9c5f6e70229f
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# MDVA-19640: Relatórios avançados não mostram dados

O patch MDVA-19640 corrige o problema quando os Relatórios avançados não mostram dados. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-19640. Observe que não há nenhum plano atual para corrigir esse problema em versões futuras.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. No Administrador, vá para **Relatórios** > **Business Intelligence** e selecione **Relatórios Avançados**.
1. Exiba a página **Relatórios Avançados**.

<u>Resultados esperados</u>:

O relatório Relatórios avançados contém informações, conforme esperado.

<u>Resultados reais</u>:

O relatório Relatórios avançados não mostra dados.

<u>Etapas adicionais necessárias após a instalação do patch</u>:

A consulta SQL a seguir deve ser aplicada para atualizar registros na tabela cron_schedule:
`UPDATE core_config_data SET path = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics") WHERE path LIKE "crontab/default/jobs/analytics%";`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

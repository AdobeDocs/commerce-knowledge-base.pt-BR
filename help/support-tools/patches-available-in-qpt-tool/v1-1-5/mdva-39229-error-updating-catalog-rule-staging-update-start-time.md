---
title: "MDVA-39229: Erro após a atualização da hora de início da atualização da Regra de catálogo"
description: O patch MDVA-39229 corrige o problema em que os usuários recebem um erro após atualizar a hora de início da atualização de Preparo da regra de catálogo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 está instalada. A ID do patch é MDVA-39229. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229: Erro após a atualização da hora de início da atualização de Preparo da regra de catálogo

O patch MDVA-39229 corrige o problema em que os usuários recebem um erro após atualizar a hora de início da atualização de Preparo da regra de catálogo. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.1.5 está instalado. A ID do patch é MDVA-39229. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários recebem um erro depois de atualizar a hora de início da atualização da Regra de catálogo Preparação.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma regra de Preço de Catálogo.
1. Crie e execute qualquer atualização de Preparo.
1. Execute a consulta e verifique se o sinalizador de Preparo foi criado.


   `select * from flag;`


1. Crie uma nova Atualização de preparo para iniciar após cinco minutos.
1. Abertura **Conteúdo** > **Estágios** > **Painel** > **Nova atualização** e atrasar a hora de início em um minuto.
1. Espere seis minutos.
1. Execute o cron.

<u>Resultados esperados</u>:

A hora de início da atualização é alterada e a atualização é aplicada. A atualização antiga é excluída do `staging_update` tabela.

<u>Resultados reais</u>:

Os usuários recebem o seguinte erro:

*report.ERROR: O trabalho Cron staging_synchronize_entities_period tem um erro: A atualização ativa não pode ser excluída.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.

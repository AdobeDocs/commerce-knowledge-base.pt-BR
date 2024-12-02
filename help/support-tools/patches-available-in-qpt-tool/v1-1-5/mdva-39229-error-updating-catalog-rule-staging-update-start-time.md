---
title: 'MDVA-39229: Erro após a atualização da hora de início da atualização de Preparo da regra de catálogo'
description: O patch MDVA-39229 corrige o problema em que os usuários recebem um erro após atualizar a hora de início da atualização de Preparo da regra de catálogo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 está instalada. A ID do patch é MDVA-39229. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229: Erro após a atualização da hora de início da atualização de Preparo da regra de catálogo

O patch MDVA-39229 corrige o problema em que os usuários recebem um erro após atualizar a hora de início da atualização de Preparo da regra de catálogo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 está instalada. A ID do patch é MDVA-39229. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários recebem um erro depois de atualizar a hora de início da atualização da Regra de catálogo Preparação.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma regra de Preço de Catálogo.
1. Crie e execute qualquer atualização de Preparo.
1. Execute a consulta e verifique se o sinalizador de Preparo foi criado.


   `select * from flag;`


1. Crie uma nova Atualização de preparo para iniciar após cinco minutos.
1. Abra **Conteúdo** > **Preparo** > **Painel** > **Nova Atualização** e atrase a hora de início em um minuto.
1. Espere seis minutos.
1. Execute o cron.

<u>Resultados esperados</u>:

A hora de início da atualização é alterada e a atualização é aplicada. A atualização antiga foi excluída da tabela `staging_update`.

<u>Resultados reais</u>:

Os usuários recebem o seguinte erro:

*report.ERROR: o trabalho do Cron staging_synchronize_entities_period tem um erro: A atualização ativa não pode ser excluída.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

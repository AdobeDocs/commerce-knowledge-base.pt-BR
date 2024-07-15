---
title: "MDVA-29389: falha no trabalho cron relacionado ao Advanced Reporting"
description: '"O patch MDVA-29389 corrige o problema em que, em Relatórios avançados, onde o cronjob "analytics_collect_data" diz: "*A porta deve ser configurada no parâmetro de host (como localhost:3306)*". Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. A ID do patch é MDVA-29389. O problema foi corrigido no Adobe Commerce 2.4.2.'''
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389: falha no trabalho cron relacionado ao Advanced Reporting

O patch MDVA-29389 corrige o problema em que, em Advanced Reporting, o cronjob `analytics_collect_data` diz: &quot;*A porta deve ser configurada dentro do parâmetro de host (como localhost:3306)*&quot;. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. A ID do patch é MDVA-29389. O problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4.

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Na instância do Adobe Commerce, ative Relatórios avançados.
1. Execute a seguinte consulta para inserir o valor analytics/general/token no BD:

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. Abra env.php e adicione a porta ao parâmetro host na configuração do banco de dados no seguinte formato: `'host' => 'hostname:port',`
1. Limpar cache.
1. Execute o trabalho cron `analytics_collect_data`.

<u>Resultados esperados</u>:

O trabalho `analytics_collect_data` é executado com êxito ao usar a porta padrão ou não padrão para se conectar ao MySQL em env.php.

<u>Resultados reais</u>:

O trabalho `analytics_collect_data` aciona um erro &quot;*A porta deve ser configurada dentro do parâmetro de host (como localhost:3306)*&quot; ao usar uma porta não padrão para se conectar ao MySQL em env.php.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

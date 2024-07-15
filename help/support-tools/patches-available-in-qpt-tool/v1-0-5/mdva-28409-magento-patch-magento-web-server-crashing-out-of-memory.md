---
title: "Patch MDVA-28409: falha do servidor Web Adobe Commerce - Memória insuficiente"
description: O patch MDVA-28409 resolve o problema em que o trabalho cron para remover cotações parou devido à necessidade de processar um grande número de itens. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5 está instalada.
exl-id: 175e5f2f-2f76-42ee-83e9-c1b23ff81e96
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Patch MDVA-28409: falha do servidor Web Adobe Commerce - Memória insuficiente

O patch MDVA-28409 resolve o problema em que o trabalho cron para remover cotações parou devido à necessidade de processar um grande número de itens. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5 está instalada.

## Produtos e versões afetados

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.4 - 2.3.5, 2.4.0

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O problema é que o trabalho cron ficou sem memória devido à quantidade de dados que o trabalho está tentando processar. Os sintomas desse problema incluem desempenho lento devido ao alto uso de disco pelo MySQL e baixa memória do servidor da Web.

<u>Etapas a serem reproduzidas:</u>

Para verificar se há um trabalho cron que não possa remover cotas desatualizadas, execute a seguinte consulta:

```
select * from cron_schedule where job_code like '%sales_clean_quotes%'
```

<u>Resultado esperado:</u>

O status do trabalho do cron `sales_clean_quotes` deve ser `success`.

<u>Resultado real:</u>

O status do trabalho do cron `sales_clean_quotes` é `running` ou `error`.

Outra maneira de confirmar se há um trabalho cron que não é capaz de remover aspas desatualizadas é mapear a saída da consulta da **Etapa 1** (`executed_at`) contra os carimbos de data/hora de qualquer erro de memória em `/var/log/cron.log`. Se houver um trabalho cron que não possa processar a quantidade de dados, você poderá ver uma mensagem semelhante a:

```
PHP Fatal error:  Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91

Fatal error: Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91
--
[2020-05-30 05:00:27.224718] Launching command 'php bin/magento cron:run'.
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

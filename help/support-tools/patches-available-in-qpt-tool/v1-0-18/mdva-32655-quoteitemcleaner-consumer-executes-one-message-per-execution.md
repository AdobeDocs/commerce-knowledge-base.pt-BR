---
title: 'MDVA-32655: o consumidor "quoteItemCleaner" executa uma mensagem por execução'
description: O patch MDVA-32655 corrige o status de mensagem "em andamento" incorreto para a mensagem "concluído" correta para o consumidor "quoteItemCleaner" após excluir vários produtos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalada. A ID do patch é 32655. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655: O consumidor &quot;quoteItemCleaner&quot; executa uma mensagem por execução

O patch MDVA-32655 corrige o status de mensagem &quot;em andamento&quot; incorreto para a mensagem &quot;completa&quot; correta para o consumidor `quoteItemCleaner` após excluir vários produtos. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalada. A ID do patch é 32655. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.3

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O consumidor `quoteItemCleaner` executa apenas uma mensagem em cada execução.

<u>Etapas a serem reproduzidas</u>:

1. Verifique a tabela de banco de dados `queue_message_status` e certifique-se de que todas as mensagens de fila existentes estejam no estado &quot;Concluído&quot; (ID de status 4).
1. Interrompa a execução automática do cron do Adobe Commerce.
1. Crie dois ou três produtos simples.
1. Faça uma exclusão em massa desses três produtos simples.
1. Na tabela `queue_message_status`, você verá três novos registros para o tópico `catalog_product_removed_queue` com ID de status 2 (novo registro).
1. Execute o seguinte comando para processar estas `catalog_product_removed_queue` mensagens pendentes:

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>Resultados esperados</u>:

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

Todos os status da mensagem `catalog_product_removed_queue` são atualizados para concluídos (ID=4).

<u>Resultados reais</u>:

Somente um registro de três é atualizado para o status &quot;Concluído&quot; (ID = 4). O status das outras duas mensagens é ID de status = 3 (em andamento). Um backlog é gerado com mensagens de fila não processadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

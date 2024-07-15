---
title: "MDVA-31590: Não é possível atualizar atributos em massa usando filas assíncronas MySQL"
description: O patch MDVA-31590 resolve o problema em que os usuários não conseguem atualizar atributos em massa usando filas assíncronas MySQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 está instalada. A ID do patch é MDVA-31590. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 57db28dd-a739-4a77-927d-6339af4fa4a6
feature: Attributes, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# MDVA-31590: Não é possível atualizar atributos em massa usando filas assíncronas MySQL

O patch MDVA-31590 resolve o problema em que os usuários não conseguem atualizar atributos em massa usando filas assíncronas MySQL. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 está instalada. A ID do patch é MDVA-31590. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0-2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários não podem atualizar atributos em massa usando o MySQL async.

<u>Etapas a serem reproduzidas</u>:

1. Na grade de produtos no back-end do, execute uma ação em massa para atualizar os valores de atributo de alguns produtos.
   * Verifique os produtos e selecione **Atualizar atributos** na lista suspensa Ações.
1. Defina valores para os atributos necessários e atribua produtos aos sites e salve.
1. Quando a página for recarregada, exibirá uma mensagem como a seguinte:
   *Tarefa &quot;Atualizar atributos para N produtos selecionados&quot;: 1 item(ns) foi(foram) agendado(s) para uma atualização.*
1. Aguarde alguns segundos e recarregue a página de backend.

<u>Resultados esperados</u>:

1. A página exibe uma mensagem de atualização bem-sucedida, como: *1 item(ns) foi(foram) atualizado(s) com êxito.*
1. Os valores de atributo para produtos relacionados são atualizados.
1. No BD, novos registros são criados nas tabelas `magento_bulk` e `magento_operation` (operações relacionadas ao lote).
1. Novos registros são criados na tabela `queue_message` (relacionada às filas `product_action_attribute.update` e/ou `product_action_attribute.website.update`).
1. A tabela `queue_message_status` tem registros com o status &quot;4&quot;.
1. NÃO há erros em `system.log`.

<u>Resultados reais</u>:

1. A página ainda exibe uma mensagem como a seguinte:
   *Tarefa &quot;Atualizar atributos para N produtos selecionados&quot;: 1 item(ns) foi(foram) agendado(s) para uma atualização.*
1. Os valores de atributo dos produtos são atualizados.
1. Um novo registro é criado na tabela `message_bulk`, mas não há registro(s) relacionado(s) na tabela `magento_operation`.
1. Novos registros são criados nas tabelas `queue_message` e `queue_message_status`.
1. A tabela `queue_message_status` possui registro com status de erro (valor de status &quot;6&quot;).
1. `system.log` contém um erro semelhante ao seguinte:
   *main.CRITICAL: Mensagem rejeitada: SQLSTATE[23000]: Violação de restrição de integridade: 1048 A coluna &#39;operation_key&#39; não pode ser nula, a consulta foi: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?, ?) [][]*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

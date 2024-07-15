---
title: "MDVA-24201: as regras de preço do catálogo não funcionam"
description: O patch MDVA-24201 resolve o problema em que as regras de preço do catálogo ativo no banco de dados não se aplicam no front-end.
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201: As regras de preço do catálogo não funcionam

O patch MDVA-24201 resolve o problema em que as regras de preço do catálogo ativo no banco de dados não se aplicam no front-end.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.3.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.3

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisito</u>:

Instale uma nova instância de Magento com dados de amostra.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no **Painel de administração** > **Marketing** > **Regra de preço de catálogo** > **Adicionar nova regra**, defina as seguintes configurações:
   1. Defina o **Nome da Regra**.
   1. Definir **Ativo** = *Não.*
   1. Definir Condições: **Categoria** = *4*. (Exemplo: Sacos)
   1. Definir ações:
      1. Definir **Aplicar como**   **porcentagem do original**.
      1. Definir **Valor do Desconto** = *10*.
      1. Salve e clique em Continuar edição.
   1. Clique em **Agendar nova atualização**:
      * Defina o **Nome da Regra**.
      * Definir **Ativo** = *Sim*.
      * Salve.
1. Vá para o back-end e execute:

   `php    bin/magento cron:run`

<u>Resultados esperados</u>:

Os preços dos produtos da categoria 4 &quot;Sacos&quot; devem ser reduzidos em 10 % do preço original, uma vez que foi fixado pela regra do preço de catálogo, conforme previsto.

<u>Resultados reais</u>:

Nenhuma alteração de preço ocorre mesmo que a regra de preço de catálogo esteja ativa.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

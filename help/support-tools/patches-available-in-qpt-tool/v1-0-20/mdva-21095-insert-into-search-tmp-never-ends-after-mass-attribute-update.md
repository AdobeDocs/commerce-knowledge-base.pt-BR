---
title: 'MDVA-21095: INSERT INTO "search_tmp..." nunca termina após a atualização do atributo de massa'
description: O patch MDVA-21095 corrige o problema quando uma consulta `INSERT INTO` "search\_tmp..." nunca termina após uma atualização de atributo em massa. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-21095. Observe que não há nenhum plano atual para corrigir esse problema em versões futuras.
exl-id: fd599473-b49a-4f9c-a13f-612d05e43f09
feature: Attributes, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-21095: INSERT INTO &quot;search_tmp...&quot; nunca termina após a atualização do atributo de massa

O patch MDVA-21095 corrige o problema quando uma consulta `INSERT INTO` &quot;search\_tmp...&quot; nunca termina após uma atualização de atributo em massa. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-21095. Observe que não há nenhum plano atual para corrigir esse problema em versões futuras.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

`INSERT INTO` &quot;search\_tmp...&quot; nunca termina após uma atualização de atributo em massa.

<u>Etapa de reprodução</u>:

Execute uma atualização dos valores do atributo em massa com ~30.000 itens.

<u>Resultados esperados</u>:

O processo de reindexação é concluído normalmente, conforme esperado.

<u>Resultados reais</u>:

O processo de reindexação é concluído, mas muitas consultas `INSERT INTO` &quot;search\_tmp...&quot; começam até que o servidor atinja o valor do parâmetro `pm.max_children` e o PHP-fpm morre, e elas constantemente reocorrem mesmo após a reinicialização do MySQL e o encerramento do processo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

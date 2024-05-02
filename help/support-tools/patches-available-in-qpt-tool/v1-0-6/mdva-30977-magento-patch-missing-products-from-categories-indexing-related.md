---
title: "MDVA-30977: produtos ausentes de categorias, relacionados à indexação"
description: O patch MDVA-30977 corrige os problemas com produtos exibidos nas páginas de categoria da loja durante as ações de reindexação ou em massa com um grande número de produtos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 está instalada. Os problemas estão programados para serem corrigidos no Adobe Commerce 2.4.2.
exl-id: 66ec4f53-c01d-4f87-a175-84f44a26f5d3
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# MDVA-30977: produtos ausentes de categorias, relacionados à indexação

O patch MDVA-30977 corrige os problemas com produtos exibidos nas páginas de categoria da loja durante as ações de reindexação ou em massa com um grande número de produtos. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O v.1.0.6 está instalado. Os problemas estão programados para serem corrigidos no Adobe Commerce 2.4.2.

## Produtos e versões afetados

O patch foi criado para o Adobe Commerce na infraestrutura em nuvem 2.3.4. Também é compatível com o Adobe Commerce no local 2.3.4.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problemas

### Problema 1

O número de produtos exibidos na página de categoria da loja é diferente após cada recarregamento de página durante a atualização de produtos em massa.

<u>Etapas a serem reproduzidas:</u>

1. Crie pelo menos 30000 produtos em duas categorias - pelo menos 15000 produtos em cada categoria.
1. Ir para **Catálogo** > **Produtos** no Administrador de comércio.
1. Selecione todos os produtos na grade e execute uma atualização de atributo em massa. Por exemplo, defina **Novo** = *Sim* atributo.
1. Execute a tarefa Magento cron usando o `bin/magento cron:run` comando duas vezes.
1. Atualize as páginas de categoria na Loja enquanto o Adobe Commerce executa a atualização de 30000 produtos.

<u>Resultado esperado:</u>

O número de produtos em categorias é sempre 15000 em cada atualização de página de categoria.

<u>Resultado real:</u>

O número de produtos em categorias é diferente em cada atualização de página de categoria.

### Problema 2

Quando o reindex completo do inventário for executado, as páginas de categoria ficarão vazias e a variável *Não é possível encontrar produtos que correspondam à seleção* será exibida.

<u>Etapas a serem reproduzidas:</u>

1. Configure o Adobe Commerce com o Elasticsearch.
1. Adicionar um novo site.
1. Crie uma nova fonte e atribua-a ao novo site usando a opção Gerenciar estoque.
1. Crie 30000 produtos configuráveis.
1. Atribua todos os produtos ao novo site e também adicione o inventário à nova origem de inventário.
1. Executar um reindexação completo.
1. Executar a reindexação de estoque executando `bin/magento indexer:reindex inventory`
1. Procure uma categoria com um grande número de produtos.

<u>Resultado esperado:</u>

As páginas de categoria exibem os produtos como de costume durante a reindexação.

<u>Resultado real:</u>

As páginas de categoria ficam vazias durante a reindexação.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.

---
title: "MDVA-11189: linhas cataloginventory_stock excluídas após importação de CSV"
description: O patch do Adobe Commerce MDVA-11189 corrige o problema ao importar um arquivo .csv para atualizar o estoque do produto; as linhas da tabela "cataloginventory_stock" são excluídas. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-1189. Observe que o problema foi corrigido no Adobe Commerce 2.3.5.
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189: linhas cataloginventory_stock excluídas após importação de CSV

O patch MDVA-11189 do Adobe Commerce corrige o problema ao importar um arquivo .csv para atualizar o estoque do produto; as linhas da tabela `cataloginventory_stock` são excluídas. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-1189. Observe que o problema foi corrigido no Adobe Commerce 2.3.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.2.3

**Compatível com as versões do Adobe Commerce:** Adobe Commerce (todos os métodos de implantação) 2.3.0-2.3.4-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige o problema ao importar um `.csv` para atualizar o estoque de produtos; as linhas da tabela `cataloginventory_stock` são excluídas.

<u>Etapas a serem reproduzidas:</u>

1. No banco de dados, execute o seguinte comando MySQL: `select count(*) from cataloginventory_stock_status;`
1. Observe o número de linhas.
1. Defina o crontab da seguinte maneira: `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. Vá para o painel Administrador em **Sistema** > **Ferramentas** > **Gerenciamento de Índice**.
1. Defina indexadores como *Atualizar por Agendamento.*
1. Vá para **Sistema** > *Transferência de Dados* > **Exportar**.
1. Definir **Tipo de Entidade** igual a *Produtos* > **Continuar**.
1. Abra o arquivo salvo `.csv` > Remover todas as colunas, exceto SKU e QTY.
1. Atualize a quantidade de todos os produtos para 150.
1. Salve o arquivo `.csv`.
1. Vá para **Sistema** > *Transferência de Dados* > **Importar**.
1. Defina os seguintes valores:
   1. Tipo de entidade: *Produtos*
   1. Comportamento de Importação: *Adicionar/Atualizar*
   1. Deixe todos os outros valores como padrão.
   1. Escolha Arquivo para selecionar a planilha de produtos do catálogo.
1. Clique em **Verificar Dados** > **Importar**. Aguarde de 5 a 10 minutos.
1. No banco de dados, execute o seguinte comando MySQL:
   `select count(*) from cataloginventory_stock_status;`

<u>Resultado real:</u>

O número de linhas em `cataloginventory_stock` é reduzido após a importação de CSV para atualizar o estoque.

<u>Resultado esperado:</u>

O número de linhas em `cataloginventory_stock` deve permanecer o mesmo após a importação do CSV para atualizar o estoque.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

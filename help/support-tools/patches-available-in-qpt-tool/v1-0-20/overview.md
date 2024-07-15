---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.0.20'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.0.20.
exl-id: 13ed85f9-4ecb-467f-9ed0-ceec4ac200db
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Visão geral do [!DNL Quality Patches Tool] (QPT) v1.0.20

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.20.

O QPT v1.0.20 inclui os seguintes patches:

1. **MC-41359**: corrige o problema das configurações incorretas de parâmetros de cookie SameSite.
1. **MDVA-11189**: corrige o problema ao importar um arquivo CSV para atualizar o estoque de produtos; as linhas da tabela `cataloginventory_stock` são excluídas.
1. **MDVA-15546**: corrige o problema em que, após a criação de uma ordem, um erro *Column entity_id where clause is ambiguous* é exibido no log de exceções.
1. **MDVA-19640**: corrige o problema em que [!DNL Advanced Reporting] não está mostrando dados.
1. **MDVA-21095**: corrige o problema quando uma consulta `INSERT INTO search_tmp` não terminará após a atualização do valor do atributo em massa.
1. **MDVA-22026**: corrige o problema em que a importação de produtos do arquivo CSV, incluindo imagens de URLs externas, falha.
1. **MDVA-22383**: corrige o problema em que salvar um produto leva muito tempo e a página é interrompida.
1. **MDVA-23845**: corrige o problema em que os modelos de email não podem ser visualizados depois que a minificação do JavaScript é habilitada.
1. **MDVA-26639**: corrige o problema em que, se um novo modelo de email de confirmação de pedido for criado, os itens de pedido estarão ausentes no email de pedido.
1. **MDVA-33168**: corrige o problema ao atualizar um atributo de produto via API; todos os outros atributos são alterados para um valor vazio.
1. **MDVA-36170**: isso corrige o problema em que a consulta do GraphQL não está sendo armazenada em cache usando a marca de cache de categoria.

Use o menu à esquerda para navegar até uma página de patch específica.

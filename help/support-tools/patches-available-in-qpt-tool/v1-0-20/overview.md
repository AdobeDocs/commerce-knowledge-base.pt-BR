---
title: '"Visão geral: [!DNL Quality Patches Tool] (QPT) v1.0.20'''
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.0.20.
exl-id: 13ed85f9-4ecb-467f-9ed0-ceec4ac200db
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.20 visão geral

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.0.20.

O QPT v1.0.20 inclui os seguintes patches:

1. **MC-41359**: corrige o problema das configurações incorretas dos parâmetros de cookie SameSite.
1. **MDVA-11189**: corrige o problema ao importar um arquivo CSV para atualizar o estoque de produtos, linhas do `cataloginventory_stock` tabela são excluídas.
1. **MDVA-15546**: corrige o problema em que, após criar um pedido, um *Coluna entity_id onde a cláusula é ambígua* um erro é exibido no log de exceções.
1. **MDVA-19640**: corrige o problema em que [!DNL Advanced Reporting] O não está mostrando dados.
1. **MDVA-21095**: corrige o problema quando uma consulta `INSERT INTO search_tmp` não terminará após a atualização do valor do atributo em massa.
1. **MDVA-22026**: corrige o problema em que a importação de produtos do arquivo CSV, incluindo imagens de URLs externos, falha.
1. **MDVA-22383**: corrige o problema em que salvar um produto leva muito tempo e a página é quebrada.
1. **MDVA-23845**: corrige o problema em que os modelos de email não podem ser visualizados após a ativação da minificação do JavaScript.
1. **MDVA-26639**: corrige o problema em que, se um novo modelo de email de confirmação de pedido for criado, os itens de pedido estarão ausentes no email de pedido.
1. **MDVA-33168**: corrige o problema ao atualizar um atributo de produto por meio da API. Todos os outros atributos são alterados para um valor vazio.
1. **MDVA-36170**: isso corrige o problema em que a consulta do GraphQL não está sendo armazenada em cache usando a tag de cache de categoria.

Use o menu à esquerda para navegar até uma página de patch específica.

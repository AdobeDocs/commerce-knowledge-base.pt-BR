---
title: '"Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.39'''
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.39

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.1.39.

O QPT v1.1.39 inclui os seguintes patches:

1. **ACSD-53704**: corrige o problema em que o histórico de saldo de pontos de premiação é calculado incorretamente após a expiração dos pontos de premiação.
1. **ACSD-53583**: melhora o desempenho da reindexação parcial do *Categoria Produtos* e *Categorias de produto* indexadores.
1. **ACSD-54026**: corrige uma mensagem de erro incorreta de um `updateCompanyRole` Solicitação GraphQL para um usuário não autorizado.
1. **ACSD-54106**: corrige o problema em que a classificação de produto de categoria por nome para caracteres com ênfase em turco está incorreta.
1. **ACSD-52219**: corrige o problema em que os filtros salvos das grades de administrador não funcionam como esperado ao alternar frequentemente entre exibições de marcadores.
1. **ACSD-54342**: corrige uma mensagem de erro incorreta *Erro na estrutura de dados: os valores são misturados* ao importar um arquivo CSV sem dados válidos.
1. **ACSD-54660**: adição de um novo atributo de entrada *sort* para classificar pedidos de clientes no GraphQL por `sort_field` e `sort_direction`.
1. **ACSD-54776**: corrige o problema em que estava desmarcado *[!UICONTROL Use Default Value]* Os valores de campo de produto e não padrão não são salvos para a segunda exibição de site, loja e loja.
1. **ACSD-53998**: corrige o problema em que uma **[!UICONTROL Dynamic Block]** com base em um **[!UICONTROL Customer Segment]** não funciona corretamente depois de fazer logoff de uma conta de cliente.
1. **ACSD-53204**: Correções *Não é possível salvar o produto.* erro ao fazer solicitações simultâneas para adicionar imagens à galeria de produtos usando o `rest/V1/products/<sku>/media` terminal.
1. **ACSD-47657**: adição de um mecanismo de armazenamento em cache para credenciais do AWS. Um provedor de credenciais agora usa o cache de Magento para armazenar em cache credenciais recuperadas do AWS para configuração EC2.

Use o menu à esquerda para navegar até uma página de patch específica.

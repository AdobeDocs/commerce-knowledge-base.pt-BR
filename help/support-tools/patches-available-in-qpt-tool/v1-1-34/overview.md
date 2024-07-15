---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.34'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.34.
feature: Tools and External Services
role: Admin
exl-id: 79998832-26cb-4c11-a505-08c3382f86d4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.34

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.34.

O QPT v1.1.34 inclui os seguintes patches:

1. **ACSD-52277**: corrige o problema em que um usuário administrador não é redirecionado corretamente após selecionar a exibição da loja ao criar uma nova ordem no administrador.
1. **ACSD-50813**: corrige o problema em que um administrador não pode adicionar produtos agrupados contendo uma barra na SKU com a funcionalidade [!UICONTROL Add Products by SKU] à ordem do administrador.
1. **ACSD-51630**: corrige o problema em que uma grande quantidade de mensagens do sistema atrasa o download de páginas de administração.
1. **ACSD-51853**: corrige o problema em que os estilos de texto copiados não são aplicados quando se usa [!DNL Page Builder].
1. **ACSD-52160**: corrige o problema em que um resultado de validação de produto em relação à regra de preço do carrinho não é avaliado corretamente, com base na condição de regra *Se um item for ENCONTRADO/NÃO ENCONTRADO no carrinho com Todas/Qualquer uma dessas condições true*.
1. **ACSD-51636**: corrige o problema em que um administrador não pode adicionar novos usuários da seção de conta do cliente apesar de ter todas as funções e permissões necessárias.
1. **ACSD-51739**: corrige o problema em que um erro é retornado quando o `structure_id` é solicitado em uma solicitação GraphQL `CompanyTeam`.
1. **ACSD-51857**: corrige o problema em que o desempenho lento do relatório cron do `aggregate_sales_report_bestsellers_data` afeta tabelas de banco de dados `sales_order` e `sales_order_item` grandes.
1. **ACSD-48448**: corrige o problema em que há um problema de condição de corrida ocorrendo durante cancelamentos de pedidos, o que causa entrada duplicada na tabela *inventory_reservation*.
1. **ACSD-52689**: corrige o problema em que as imagens não podem ser carregadas no armazenamento do [!DNL Amazon S3] usando a API REST.

Use o menu à esquerda para navegar até uma página de patch específica.

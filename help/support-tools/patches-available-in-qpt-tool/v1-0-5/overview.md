---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.0.5'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.5.
exl-id: 439358e8-d6bc-4d35-aee1-f4fc33ae267c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Visão geral do [!DNL Quality Patches Tool] (QPT) v1.0.5

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.5.

O QPT v1.0.5 inclui os seguintes patches:

1. **MDVA-28191**: corrige o problema em que nenhum método de pagamento é carregado durante a criação do pedido por meio do Administrador.
1. **MDVA-28409**: corrige o problema em que o trabalho cron `sales_clean_quotes` falha com o erro *memória insuficiente* quando o número de aspas expiradas no banco de dados é enorme.
1. **MDVA-28661**: corrige o problema em que um erro é lançado na seção de conta da empresa de Usuários da Empresa depois que o administrador da empresa é alterado.
1. **MDVA-28763**: corrige o problema em que a imagem do produto está sendo duplicada após atualizar as informações do produto usando a API REST mais de uma vez.
1. **MDVA-29042**: corrige o problema em que as permissões do Catálogo foram alteradas para *Permitir* automaticamente depois que o novo produto foi adicionado ao catálogo compartilhado.
1. **MDVA-29959**: corrige o problema em que um usuário administrador restrito com permissões de *Empresas* não tem permissão para excluir a conta da empresa.
1. **MDVA-30107**: corrige o problema em que o alternador de repositório não funciona como esperado se forem usadas diferentes URLs base para exibições de repositório.
1. **MDVA-30265**: corrige o problema em que o link de rastreamento de remessa para de funcionar após a criação da fatura.
1. **MDVA-30284**: corrige o problema em que o indexador da Pesquisa de Catálogo falha devido ao seguinte erro *[!DNL Elasticsearch]: o limite total de campos no índice foi excedido.*
1. **MDVA-30428**: corrige o problema em que os clientes não podem adicionar um produto à lista de desejos se esse produto estiver atribuído a uma origem de estoque personalizada.
1. **MDVA-30593**: corrige o problema em que as cotações expiradas de acordo com a configuração Tempo de Vida da Cotação não são limpas.

Use o menu à esquerda para navegar até uma página de patch específica.

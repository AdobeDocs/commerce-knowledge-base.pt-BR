---
title: '"Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.12'''
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.1.12.
exl-id: 749dbfd5-9ded-4919-8c57-0f66c85751e9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.1.12 visão geral

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.1.12.

O QPT v1.1.12 inclui os seguintes patches:

1. **MDVA-39546**: corrige o problema em que a data de início da atualização de preparo podia ser definida como uma data anterior à data atual durante a edição.
1. **MDVA-39713**: corrige o problema em que o usuário pode editar a hora de início de uma atualização agendada ativa.
1. **MDVA-39993**: corrige o problema em que as alterações de inventário feitas por meio da API não refletem na página do produto no front-end.
1. **MDVA-41136**: corrige o problema em que a data de expiração do `mage-cache-sessid` não é estendido, resultando na limpeza dos dados do cliente.
1. **MDVA-41229**: corrige o problema em que as imagens disponíveis no back-end do não são exibidas no front-end após a importação de produtos configuráveis.
1. **MDVA-41628**: corrige o problema em que usuários administradores restritos existentes obtêm acesso aos novos recursos quando novos módulos são adicionados.
1. **MDVA-42410**: corrige o problema em que os relatórios de cupom exibem somente a moeda base padrão.
1. **MDVA-42645**: corrige o problema em que o Administrador não pode reembolsar pontos de premiação se a funcionalidade de crédito da loja estiver desativada.
1. **MDVA-42689**: corrige o problema em que o Adobe Commerce lança um *Violação de Restrição de Integridade* erro ao atualizar categorias de produto durante a importação.
1. **MDVA-42855**: corrige o problema em que um novo endereço de cliente não é salvo no catálogo de endereços durante o check-out.
1. **MDVA-42950**: corrige o problema em que os vídeos não são reproduzidos na página do produto.
1. **MDVA-43232**: corrige o problema em que a classificação de produtos no [!DNL Visual Merchandiser] Por Preço Especial para Baixo/Superior causa um erro ao salvar a categoria.
1. **MDVA-43348**: corrige o problema em que a solicitação do GraphQL com cartão-presente mostra um erro, se `gift_card_options` contain *uid*.
1. **MDVA-43414**: corrige o erro fatal do PHP que ocorre ao executar o `inventory.reservations.updateSalabilityStatus` consumidor de fila em SKUs numéricas.
1. **MDVA-43726**: corrige o problema em que a regra de preço do Catálogo com base na correspondência de atributos no nível do armazenamento falha ao ser aplicada após a reindexação parcial.
1. **MDVA-43731**: corrige o problema em que *Pesquisar Sinônimos* não funciona mais quando o valor é adicionado em *Termos mínimos para corresponder*.

Use o menu à esquerda para navegar até uma página de patch específica.

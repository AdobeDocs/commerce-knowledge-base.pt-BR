---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.12'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.12.
exl-id: 749dbfd5-9ded-4919-8c57-0f66c85751e9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Visão geral da v1.1.12 do [!DNL Quality Patches Tool] (QPT)

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.12.

O QPT v1.1.12 inclui os seguintes patches:

1. **MDVA-39546**: corrige o problema em que a data de início da atualização de preparo poderia ser definida como uma data anterior à data atual durante a edição.
1. **MDVA-39713**: corrige o problema em que o usuário pode editar a hora de início de uma atualização agendada ativa.
1. **MDVA-39993**: corrige o problema em que as alterações de inventário feitas por meio da API não refletem na página do produto no front-end.
1. **MDVA-41136**: corrige o problema em que a data de expiração de `mage-cache-sessid` não é estendida, resultando na limpeza dos dados do cliente.
1. **MDVA-41229**: corrige o problema em que as imagens disponíveis no back-end não são exibidas no front-end após a importação de produtos configuráveis.
1. **MDVA-41628**: corrige o problema em que usuários administradores restritos existentes obtêm acesso aos novos recursos quando novos módulos são adicionados.
1. **MDVA-42410**: corrige o problema em que os relatórios de cupom exibem somente a moeda base padrão.
1. **MDVA-42645**: corrige o problema em que o Administrador não pode reembolsar pontos de premiação se a funcionalidade de crédito de armazenamento estiver desabilitada.
1. **MDVA-42689**: corrige o problema em que o Adobe Commerce lança um erro de *Violação de Restrição de Integridade* ao atualizar categorias de produto durante a importação.
1. **MDVA-42855**: corrige o problema em que um novo endereço de cliente não é salvo no catálogo de endereços durante o check-out.
1. **MDVA-42950**: corrige o problema em que os vídeos não são reproduzidos na página do produto.
1. **MDVA-43232**: corrige o problema em que a classificação de produtos em [!DNL Visual Merchandiser] por Preço Especial/Inferior/Superior causa um erro ao salvar a categoria.
1. **MDVA-43348**: corrige o problema em que a solicitação GraphQL de cartão-presente mostra um erro se `gift_card_options` contiver *uid*.
1. **MDVA-43414**: corrige o erro fatal de PHP que ocorre ao executar o consumidor da fila `inventory.reservations.updateSalabilityStatus` em SKUs numéricas.
1. **MDVA-43726**: corrige o problema em que a regra de preço de catálogo com base na correspondência de atributo de nível de repositório falha ao ser aplicada após a reindexação parcial.
1. **MDVA-43731**: corrige o problema em que os *Sinônimos de Pesquisa* não funcionam mais quando o valor é adicionado em *Termos Mínimos para Correspondência*.

Use o menu à esquerda para navegar até uma página de patch específica.

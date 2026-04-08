---
title: Alterar endereço de email atual da conta do Adobe
description: Saiba como alterar o endereço de email atual registrado na conta do Adobe para um novo endereço atualmente não registrado na conta do Adobe ou da Magento.
exl-id: ca549d38-0d62-4206-9727-0ed85b733dc3
feature: Communications
source-git-commit: 2fc3353c7563cff6fb82236d40a91306523a579e
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Alterar endereço de email atual da conta do Adobe

Este artigo explica como alterar o endereço de email atual registrado na [conta do Adobe](https://account.adobe.com/) para um novo endereço atualmente não registrado na [conta do Adobe](https://account.adobe.com/) ou na [conta do Magento](https://account.magento.com/).

## Produtos e versões afetados

* Adobe Commerce (todos os métodos e versões de implantação)

## Pré-requisitos

O proprietário do novo endereço de email deve ter acesso ao endereço de email atual.

Se você não tiver acesso ao endereço de email atual, configure o encaminhamento de email do email do proprietário atual para um novo email usando a configuração do servidor de email da empresa.

## Etapas para alterar o endereço de email

Siga estas etapas para alterar o endereço de email:

1. Redefina a senha usada com o endereço de email antigo. Siga as instruções fornecidas em [Redefinir senha esquecida](https://helpx.adobe.com/br/manage-account/using/change-or-reset-password.html) na Adobe helpx.
1. O link de redefinição de senha é enviado para a caixa de correio do proprietário atual com instruções.
1. Navegue até a [página da conta do Adobe](https://account.adobe.com) para fazer logon com o novo email e configurar a senha.

## Importante: o nome de usuário da conta na nuvem não é atualizado automaticamente

Se você usa o Adobe Commerce na infraestrutura em nuvem, alterar o endereço de email na sua conta Adobe ou ID MAGE não atualiza automaticamente o nome de usuário mostrado na sua [conta da nuvem](https://accounts.magento.cloud).

Após concluir as etapas deste artigo para alterar o endereço de email da sua conta da Adobe:

1. Faça logon na sua conta da nuvem em [https://accounts.magento.cloud](https://accounts.magento.cloud).
1. Atualize manualmente o perfil da conta da nuvem (nome de usuário) seguindo as etapas em [Como atualizar o perfil da conta da nuvem](/help/how-to/general/how-to-update-the-cloud-account-profile.md) em nossa base de dados de conhecimento de suporte.

Isso garante que o nome de usuário da sua conta da Cloud permaneça alinhado ao email atualizado da Adobe ou da MAGE ID e evita confusão ao acessar projetos na nuvem ou receber notificações do sistema.

## Verificar o acesso ao Marketplace e ao Suporte após a alteração do email

Depois de alterar o endereço de email da sua ID do MAGE, você também deve concluir as seguintes etapas para garantir que o Adobe Commerce Marketplace e o Suporte reconheçam corretamente o seu novo email:

### Verificar email do Commerce Marketplace

1. Faça logon em [https://commercemarketplace.com/customer/account](https://commercemarketplace.com/customer/account) e confirme se o email da sua conta foi atualizado para o novo endereço.
1. Se o email não tiver sido atualizado, envie um [Tíquete de suporte](https://experienceleague.adobe.com/pt-br/support#home) solicitando que o email da conta Commerce Marketplace seja corrigido.

### Peça ao suporte para finalizar as atualizações da conta interna

1. Envie um [Tíquete de suporte](https://experienceleague.adobe.com/pt-br/support#home) solicitando a conclusão de todas as atualizações internas necessárias (por exemplo, atualização da vinculação entre as novas e antigas Adobe IDs e a sua MAGE ID).
1. Se você já tiver aberto um tíquete de suporte porque o email do Commerce Marketplace não foi atualizado na seção anterior, poderá usar o mesmo tíquete para solicitar essas atualizações internas adicionais.

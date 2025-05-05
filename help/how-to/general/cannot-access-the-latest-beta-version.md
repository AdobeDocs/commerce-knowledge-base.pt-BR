---
title: Não é possível acessar a versão mais recente do Beta
description: Este artigo fornece soluções para problemas que ocorrem ao tentar utilizar as versões mais recentes do Beta para o Adobe Commerce. O código Beta só está disponível para parceiros Adobe oficiais que tenham seguido o processo descrito no [Programa Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Não é possível acessar a versão mais recente do Beta

Este artigo fornece soluções para problemas que ocorrem ao tentar utilizar as versões mais recentes do Beta para o Adobe Commerce. O código Beta só está disponível para parceiros Adobe oficiais que tenham seguido o processo descrito no [Programa Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Problema

Este artigo aborda os seguintes problemas de acesso ao código de acesso antecipado:

* A versão do Adobe Commerce Beta não está disponível para download em **Minha Conta** > **Downloads** em [magento.com](https://account.magento.com/customer/account/login).
* Falha ao baixar a versão do Adobe Commerce de acesso antecipado de [magento.com](https://account.magento.com/customer/account/login) usando o Composer.

## Causa

Estas são as causas mais comuns de problemas:

* Você está procurando o código de acesso antecipado no local errado.
* Você está usando o MageID incorreto.
* O desenvolvedor precisa das chaves de acesso da MageID correta.
* Sua conta não faz parte do programa Beta.

## Solução

### Localização do código de acesso antecipado

Durante os períodos de acesso beta, os pacotes de versão só estão disponíveis via Composer no [repo.magento.com](https://repo.magento.com/). Os pacotes de versão não estão disponíveis nos portais GitHub e Adobe Commerce durante esse período, e nós os publicaremos nesses locais na data de disponibilidade geral. Para obter mais detalhes sobre como usar o Composer, clique [aqui](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/composer).

### ID da imagem que você precisa usar

Você deve usar a MageID principal associada à sua conta de parceiro. O programa Beta não está vinculado a nenhum contato com acesso compartilhado. O acesso antecipado só pode ser acessado via Composer ou [repo.magento.com](https://repo.magento.com/) pela MageID associada à sua licença de parceiro.

#### Como descobrir se minha MageID é a principal?

Para descobrir se a MageID é primária, tente o seguinte:

1. Faça logon em [magento.com](https://account.magento.com/customer/account/login) e vá para a guia **Meus Produtos e Serviços**. Na subseção Parceiros, verifique se você vê as informações da licença ativa do Parceiro:
   * Se você vir as informações ativas da licença do Partner, sua MageID é a principal. A licença do Parceiro estará ativa se o valor DATA FINAL for uma data futura.
   * Se você não vir as informações ativas da licença do Partner, sua MageID terá somente acesso compartilhado. Para descobrir quem é o detentor da ID primária, vá para **Compartilhado(s) comigo** Observe o SHARENAME especificado. Clique em **Alternar contas** e selecione o valor anotado em SHARENAME. Na página de boas-vindas, você verá o email do titular da ID principal.
1. Se, por qualquer motivo, você não conseguir encontrar essas informações em [magento.com](https://account.magento.com/customer/account/login), entre em contato com seu Gerente de Parceiros.
1. Se nenhuma das situações acima funcionar, [contate o Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### O desenvolvedor não tem acesso correto às chaves

Se você for o proprietário primário da MageID e precisar conceder acesso a um desenvolvedor da sua equipe, siga as etapas abaixo:

1. Faça com que o proprietário primário do MageID entre em [account.magento.com](https://account.magento.com/customer/account/login).
1. Selecione a guia **Marketplace** e clique em **Chaves de Acesso**.
1. Selecione **Criar uma Nova Chave de Acesso** e nomeie-a.
1. Envie as chaves para o desenvolvedor.

### Não faz parte do programa de acesso antecipado

Nosso programa Beta Access está disponível apenas para nossos parceiros técnicos e de soluções, para que eles possam avaliar nosso código de pré-produção. Para ser incluída no programa Beta Access, sua organização deve ter uma conta de Parceiro de Adobe ativa e ter assinado o NDA da Beta [aqui](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Se você acha que atende a estes critérios e não pode acessar o código beta, contate [commercebeta@adobe.com](mailto:commercebeta@adobe.com).

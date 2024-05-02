---
title: Não é possível acessar a versão Beta mais recente
description: Este artigo fornece soluções para problemas que ocorrem ao tentar utilizar as versões Beta mais recentes do código do Adobe Commerce. O código beta só está disponível para parceiros Adobe oficiais que tenham seguido o processo descrito no [Programa Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Não é possível acessar a versão Beta mais recente

Este artigo fornece soluções para problemas que ocorrem ao tentar utilizar as versões Beta mais recentes do código do Adobe Commerce. O código beta só está disponível para parceiros Adobe oficiais que tenham seguido o processo descrito em [Programa Beta do Adobe Commerce](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Problema

Este artigo aborda os seguintes problemas de acesso ao código de acesso antecipado:

* A versão Beta do Adobe Commerce não está disponível para download em **Minha conta** > **Downloads** em [magento.com](https://account.magento.com/customer/account/login).
* Falha ao baixar a versão do Adobe Commerce de acesso antecipado de [magento.com](https://account.magento.com/customer/account/login) usando o Composer.

## Causa

Estas são as causas mais comuns de problemas:

* Você está procurando o código de acesso antecipado no local errado.
* Você está usando o MageID incorreto.
* O desenvolvedor precisa das chaves de acesso da MageID correta.
* Sua conta não faz parte do programa Beta.

## Solução

### Localização do código de acesso antecipado

Durante os períodos de acesso beta, os pacotes de versão só estão disponíveis por meio do Composer no [repo.magento.com](https://repo.magento.com/). Os pacotes de versão não estão disponíveis nos portais GitHub e Adobe Commerce durante esse período, e nós os publicaremos nesses locais na data de disponibilidade geral. Para obter mais detalhes sobre como usar o Composer, clique [aqui](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html).

### ID da imagem que você precisa usar

Você deve usar a MageID principal associada à sua conta de parceiro. O programa Beta não está vinculado a nenhum contato com acesso compartilhado. O acesso antecipado só pode ser acessado pelo Composer ou [repo.magento.com](https://repo.magento.com/) pela MageID associada à sua licença de Parceiro.

#### Como descobrir se minha MageID é a principal?

Para descobrir se a MageID é primária, tente o seguinte:

1. Efetue logon no [magento.com](https://account.magento.com/customer/account/login) e vá para a página **Meus produtos e serviços** guia. Na subseção Parceiros, verifique se você vê as informações da licença ativa do Parceiro:
   * Se você vir as informações ativas da licença do Partner, sua MageID é a principal. A licença do Parceiro estará ativa se o valor DATA FINAL for uma data futura.
   * Se você não vir as informações ativas da licença do Partner, sua MageID terá somente acesso compartilhado. Para descobrir quem é o detentor da ID primária, acesse o **Compartilhado comigo** Observe o SHARENAME especificado lá. Clique em **Trocar contas** e selecione o valor anotado em SHARENAME. Na página de boas-vindas, você verá o email do titular da ID principal.
1. Se, por qualquer motivo, você não conseguir encontrar essas informações em [magento.com](https://account.magento.com/customer/account/login), entre em contato com seu gerente de parceiros.
1. Se nenhuma das opções acima funcionar, [entre em contato com o Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### O desenvolvedor não tem acesso correto às chaves

Se você for o proprietário primário da MageID e precisar conceder acesso a um desenvolvedor da sua equipe, siga as etapas abaixo:

1. Faça com que o proprietário primário da MageID faça logon no [account.magento.com](https://account.magento.com/customer/account/login).
1. Selecione o **Marketplace** e clique em **Teclas de acesso**.
1. Selecionar **Criar uma nova chave de acesso** e nomeie-o.
1. Envie as chaves para o desenvolvedor.

### Não faz parte do programa de acesso antecipado

Nosso programa de acesso beta está disponível somente para nossos Parceiros técnicos e de soluções, para que eles possam avaliar nosso código de pré-produção. Para ser incluída no programa Acesso Beta, sua organização deve ter uma conta de Parceiro Adobe ativa que esteja em bom estado e tenha assinado o NDA Beta [aqui](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Se você acha que atende a esses critérios e não pode acessar o código beta, entre em contato com [commercebeta@adobe.com](mailto:commercebeta@adobe.com).

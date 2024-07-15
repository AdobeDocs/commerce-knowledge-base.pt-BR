---
title: Não é possível acessar o pré-lançamento mais recente do Adobe Commerce
description: Este artigo fornece soluções para problemas que ocorrem ao tentar utilizar o código de pré-lançamento mais recente do Adobe Commerce.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Não é possível acessar o pré-lançamento mais recente do Adobe Commerce

Este artigo fornece soluções para problemas que ocorrem ao tentar utilizar o código de pré-lançamento mais recente do Adobe Commerce.

>[!NOTE]
>
>Se tiver problemas com o acesso ao Beta, consulte o artigo [Não é possível acessar a versão mais recente do Beta](/help/how-to/general/cannot-access-the-latest-beta-version.md).

## Problema

Este artigo aborda os seguintes problemas com o acesso ao código de pré-lançamento:

* Não é possível localizar o código de pré-lançamento.
* Falha ao baixar a versão do Adobe Commerce de acesso antecipado de [magento.com](https://account.magento.com/customer/account/login) usando o Composer.

## Causa

Estas são as causas mais comuns de problemas:

* Você está procurando o código de acesso antecipado no local errado.
* Você está usando a MageID incorreta ao acessar o código pelo Composer.
* Sua conta não faz parte do programa de pré-lançamento.

## Solução

### Localização do código de acesso antecipado

Durante o pré-lançamento, os pacotes de versão estão disponíveis em dois locais:

1. Através do Composer em [magento.com](https://repo.magento.com/) usando o MageID principal da conta. Para obter mais detalhes sobre como usar o Composer, consulte [Instalar o Adobe Commerce usando o Composer](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) na documentação do desenvolvedor.
1. **Minha Conta** > **Downloads** em [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>Os pacotes de versão não estarão disponíveis no GitHub até a data de disponibilidade geral.

### ID da imagem que você precisa usar

Você deve usar a MageID principal associada à sua conta do Adobe Commerce ou Partner. O programa de pré-lançamento não está vinculado a nenhum contato com acesso compartilhado. O acesso antecipado só pode ser acessado via Composer ou [repo.magento.com](https://repo.magento.com/) pela MageID associada à sua licença do Adobe Commerce ou licença de parceiro.

#### Como descobrir se minha MageID é a principal?

**Para comerciantes**

Para descobrir se a MageID é primária, tente o seguinte:

1. Faça logon em [magento.com](https://account.magento.com/customer/account/login) e vá para a guia **Meus Produtos e Serviços**. Verifique se você vir as informações de licença da Adobe Commerce lá:
   * Se você vir as informações de licença do Adobe Commerce, sua MageID é a principal.
   * Se você não vir as informações da licença do Adobe Commerce, sua ID de imagem terá somente acesso compartilhado. Para descobrir quem é o detentor da ID primária, vá para **Compartilhado(s) comigo** Observe o SHARENAME especificado. Clique em **Alternar contas** e selecione o valor anotado em SHARENAME. Na página de boas-vindas, você verá o email do titular da ID principal.
1. Se, por qualquer motivo, você não conseguir encontrar essas informações em [magento.com](https://account.magento.com/customer/account/login), entre em contato com a equipe de conta do Adobe.
1. Se nenhuma das situações acima funcionar, [contate o Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

**Para parceiros**

Para descobrir se a MageID é primária, tente o seguinte:

1. Faça logon em [magento.com](https://account.magento.com/customer/account/login) e vá para a guia **Meus Produtos e Serviços**. Na subseção Parceiros, verifique se você vê as informações da licença ativa do Parceiro:
   * Se você vir as informações ativas da licença do Partner, sua MageID é a principal. A licença do Parceiro estará ativa se o valor DATA FINAL for uma data futura.
   * Se você não vir as informações ativas da licença do Partner, sua MageID terá somente acesso compartilhado. Para descobrir quem é o detentor da ID primária, vá para **Compartilhado(s) comigo** Observe o SHARENAME especificado. Clique em **Alternar contas** e selecione o valor anotado em SHARENAME. Na página de boas-vindas, você verá o email do titular da ID principal.
1. Se, por qualquer motivo, você não conseguir encontrar essas informações em [magento.com](https://account.magento.com/customer/account/login), entre em contato com seu Gerente de Parceiros.
1. Se nenhuma das opções acima funcionar, [сentre em contato com o Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Não faz parte do programa de pré-lançamento

Para ser incluída no programa de acesso de pré-lançamento, sua organização deve ter uma conta ativa da Adobe Commerce ou de um parceiro em bom estado. Se você acha que atende a este critério e não pode acessar o código de pré-lançamento, [contate o Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) com sua MageID.

---
title: Problemas de implantação relacionados às permissões de conta e chaves de acesso
description: Este artigo fornece uma solução para problemas com a implantação do Adobe Commerce na infraestrutura em nuvem causados pelo conflito de acesso à propriedade principal.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Problemas de implantação relacionados às permissões de conta e chaves de acesso

Este artigo fornece uma solução para problemas com a implantação do Adobe Commerce na infraestrutura em nuvem causados pelo conflito de acesso à propriedade principal.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões compatíveis

## Problema

<u>Pré-requisitos</u>:

A licença da nuvem está associada ao Contato A (endereço de email: *<u>first@e.mail</u>*)

<u>Etapas a serem reproduzidas</u>:

1. Entre em contato com uma Adobe Commerce criada e instale as chaves de acesso na conta (Chave X).
1. O contato B (endereço de email: *<u>second@e.mail</u>*) comprou uma extensão usando sua conta e criou as chaves de acesso para instalar a extensão (Chave Y).
1. O contato A deixou a empresa e a licença (propriedade) foi transferida para o contato B.
1. O integrador de sistemas tenta instalar a extensão no ambiente de nuvem usando a Chave X.

<u>Resultado esperado</u>:

Extensão instalada com êxito.

<u>Resultado real</u>:

A extensão não está instalada porque a implantação falhou.

## Causa

Ambas as chaves são atribuídas à função de contato, o que causa um conflito.

## Solução

Se uma implantação falhar depois que uma alteração for feita no contato principal da conta (com a conta original e a nova conta tendo cada uma suas próprias chaves de acesso) e as chaves tiverem sido transferidas da conta original para a nova conta, será necessário desativar as chaves da conta original. No que diz respeito ao exemplo acima, a tecla X deve ser desativada.

### Como desativar a chave de acesso

Se você não tiver acesso à conta [Commerce Marketplace](https://marketplace.magento.com/) associada à chave antiga, [contate o Suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para desabilitar a chave.

Se você tiver acesso à conta do Marketplace associada à chave antiga, siga estas etapas para desabilitar a chave:

1. Faça logon no [Commerce Marketplace](https://marketplace.magento.com/) usando as credenciais da conta antiga.
1. Clique no nome da conta no canto superior direito da página e selecione **Meu perfil**.
1. Clique em **Teclas de Acesso** na guia Marketplace.

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Clique em **Desabilitar** ao lado da chave de acesso.

## Leitura relacionada

* [Obtenha suas chaves de autenticação](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) em nossa documentação para desenvolvedores.

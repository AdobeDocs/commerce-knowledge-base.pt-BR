---
title: Erro ao validar as credenciais do Fastly
description: Este artigo fornece uma solução para o problema em que um usuário recebe um erro ao validar as credenciais do Fastly.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 831a928dbe8fd6b37f3fe9ad5dc35ee80e11a578
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Erro ao validar as credenciais do Fastly

Este artigo fornece uma solução para o problema em que um usuário recebe um erro ao validar as credenciais do Fastly.

## Problema

O usuário recebe um erro ao validar as credenciais do Fastly.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação): todas as versões
* Extensão ou tecnologia (Fastly, New Relic etc.) version Fastly

## Solução

1. Verifique se você tem a ID de serviço Fastly e o token da API e tente validar novamente. Para instruções detalhadas, consulte [Testar as credenciais do Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#test-the-fastly-credentials) na documentação do desenvolvedor.
1. Se a verificação das credenciais falhar, execute o seguinte comando curl para confirmar o status do serviço:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Se o comando acima retornar um erro semelhante a: *{&quot;msg&quot;:&quot;Token $TOKEN expirado em 28/9/2021:03:37Z&quot;}*, envie um tíquete de suporte para solicitar um novo token de API.

   Para saber como enviar um tíquete de suporte, consulte [Guia do usuário da Central de ajuda do Adobe Commerce > TÍQUETES DE SUPORTE](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) em nossa base de conhecimento de suporte.

   >[!NOTE]
   >
   >Nunca compartilhe senhas ou tokens de API válidos/ativos diretamente no ticket, pois precisaremos revogar o token atual e gerar um novo por motivos de segurança.

1. Se o comando não retornar o erro, verifique se você está executando a versão mais recente do [!DNL Fastly] extensão. Se você estiver em uma versão anterior a 1.2.203, clique primeiro em **[!UICONTROL Save Config]** antes de testar as credenciais.

## Leituras relacionadas em nossa documentação do desenvolvedor:

* [Nuvem para Adobe Commerce > Fastly > Conta de serviço e credenciais do Fastly](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html#fastly-service-account-and-credentials)

* [Nuvem para Adobe Commerce > Configurar o Fastly > Testar as credenciais do Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#test-the-fastly-credentials)

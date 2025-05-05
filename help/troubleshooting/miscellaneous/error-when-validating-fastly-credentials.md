---
title: Erro ao validar as credenciais do Fastly
description: Este artigo fornece uma solução para o problema em que um usuário recebe um erro ao validar as credenciais do Fastly.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
* Extensão ou versão de tecnologia (Fastly, New Relic etc.) Fastly

## Solução

1. Verifique se você tem a ID de serviço Fastly e o token da API e tente validar novamente. Para obter instruções detalhadas, consulte [Testar as credenciais do Fastly](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials) na documentação do desenvolvedor.
1. Se a verificação das credenciais falhar, execute o seguinte comando curl para confirmar o status do serviço:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Se o comando acima retornar um erro semelhante a: *{&quot;msg&quot;:&quot;Token $TOKEN expirado em 2021-09-28T02:03:37Z&quot;}*, envie um tíquete de suporte para solicitar um novo token de API.

   Para saber como enviar um tíquete de suporte, consulte [Guia do Usuário da Central de Ajuda da Adobe Commerce > TÍQUETES DE SUPORTE](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) em nossa base de dados de conhecimento de suporte.

   >[!NOTE]
   >
   >Nunca compartilhe senhas ou tokens de API válidos/ativos diretamente no ticket, pois precisaremos revogar o token atual e gerar um novo por motivos de segurança.

1. Se o comando não retornar o erro, verifique se você está executando a versão mais recente da extensão [!DNL Fastly]. Se você estiver em uma versão anterior a 1.2.203, deverá clicar primeiro em **[!UICONTROL Save Config]** antes de testar as credenciais.

## Leituras relacionadas em nossa documentação do desenvolvedor:

* [Nuvem para Adobe Commerce > Fastly > Conta de serviço e credenciais do Fastly](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/fastly#fastly-service-account-and-credentials)

* [Cloud para Adobe Commerce > Configurar o Fastly > Testar as credenciais do Fastly](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials)

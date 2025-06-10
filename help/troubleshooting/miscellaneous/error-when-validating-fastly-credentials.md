---
title: 'Erro ao validar as credenciais  [!DNL Fastly] '
description: Este artigo fornece uma solução para o problema em que um usuário recebe um erro ao validar as credenciais do  [!DNL Fastly] .
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 838f0c5d55c29d026dc37a8f7e5214b9880a4353
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Erro ao validar as credenciais [!DNL Fastly]

Este artigo explica como resolver erros de *Token expirado* encontrados ao validar credenciais [!DNL Fastly].

As etapas descritas neste artigo também se aplicam se você precisar girar (alternar) o token de API [!DNL Fastly] por motivos de segurança. Nesses casos, você deve enviar um tíquete de Suporte da Adobe Commerce para solicitar um novo token de API [!DNL Fastly].

## Problema

* Você recebe um erro ao validar as credenciais do [!DNL Fastly].
* Você suspeita que o token [!DNL Fastly] pode ter sido comprometido, por exemplo, se ele tiver sido compartilhado inadvertidamente em um tíquete de suporte ou postado em um fórum público.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação): todas as versões
* Versão [!DNL Fastly] de extensão ou tecnologia ([!DNL Fastly], [!DNL New Relic] etc.)

## Solução

1. Verifique se você tem a ID de serviço e o token de API [!DNL Fastly] corretos e tente validar novamente. Para obter instruções detalhadas, consulte [Testar as [!DNL Fastly] credenciais](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials) na documentação do desenvolvedor.
1. Se a verificação das credenciais falhar, execute o seguinte comando curl para confirmar o status do serviço:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Se o comando acima retornar um erro semelhante a: `{"msg":"Token $TOKEN expired at 2021-09-28T02:03:37Z"}`, envie um tíquete de suporte para solicitar um novo token de API. Depois de receber o novo token, atualize a configuração no ambiente.

   Para saber como enviar um tíquete de suporte, consulte [Guia do Usuário da Central de Ajuda da Adobe Commerce > TÍQUETES DE SUPORTE](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) em nossa base de dados de conhecimento de suporte.

   >[!NOTE]
   >
   >Nunca compartilhe senhas ou tokens de API válidos/ativos diretamente no ticket, pois precisaremos revogar o token atual e gerar um novo por motivos de segurança.
   >
   >O Suporte da Adobe Commerce tem acesso aos tokens, portanto, não é necessário incluir essas informações no ticket.

1. Se o comando não retornar o erro, verifique se você está executando a versão mais recente da extensão [!DNL Fastly]. Se você estiver em uma versão anterior a 1.2.203, deverá clicar primeiro em **[!UICONTROL Save Config]** antes de testar as credenciais.

## Leituras relacionadas em nossa documentação do desenvolvedor:

* [Nuvem para Adobe Commerce > [!DNL Fastly] > [!DNL Fastly] conta de serviço e credenciais](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/fastly?lang=en#fastly-service-account-and-credentials)

* [Nuvem para Adobe Commerce > Configurar [!DNL Fastly] > Testar as [!DNL Fastly] credenciais](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)

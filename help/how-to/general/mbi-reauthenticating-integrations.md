---
title: 'MBI: Reautenticação de integrações'
description: Este artigo fornece soluções para reautorizar uma integração a fim de conceder à Magento Business Intelligence (MBI) os privilégios necessários para extrair dados de um serviço de terceiros. A reautorização é necessária quando esses privilégios são revogados.
exl-id: c608d6f9-64a5-44f8-9d7b-9a85a2668775
feature: Commerce Intelligence, Integration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3cd14413-6539-5c64-b063-fdcabf03abff
    internal-label: Commerce Intelligence
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%
---
# MBI: Reautenticação de integrações

Este artigo fornece soluções para reautorizar uma integração a fim de conceder à Magento Business Intelligence (MBI) os privilégios necessários para extrair dados de um serviço de terceiros. A reautorização é necessária quando esses privilégios são revogados.

## Integrações de banco de dados e SaaS

Para obter listas de integrações de banco de dados e SaaS, consulte [Conectando dados externos usando uma integração](https://experienceleague.adobe.com/pt-br/docs/commerce-business-intelligence/mbi/analyze/saas/integrations) na documentação do desenvolvedor. (Ao abrir a página, use o índice à esquerda para navegação).

## Problemas de conexão?

A autorização de uma integração concede ao MBI os privilégios necessários para extrair dados de um serviço de terceiros. A reautorização é necessária quando esses privilégios são revogados.

Isso pode ocorrer devido a várias razões:

* um problema com o serviço de terceiros
* expiração do token de autenticação
* uma alteração feita em sua conta administrativa
* ou um problema interno no MBI

O status de todas as integrações está na página Integrações ( **Gerenciar dados > Integrações** ):

![Página_de_integrações.png](assets/Integrations_page.png)

Para autenticar novamente, talvez seja necessário inserir novamente as credenciais da conta. Em alguns casos, pode ser necessário gerar novas chaves de API para a integração do problema. Clique no nome da integração do problema para iniciar o processo de reautorização.

Se o problema persistir, [envie um tíquete de suporte](https://experienceleague.adobe.com/pt-br/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).

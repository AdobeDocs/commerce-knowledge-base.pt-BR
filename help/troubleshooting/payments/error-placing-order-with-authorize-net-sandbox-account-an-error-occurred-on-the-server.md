---
title: Erro ao fazer pedido com a conta de sandbox Authorize.net (ocorreu um erro no servidor)
description: Este artigo fornece uma correção para a mensagem de erro "*Ocorreu um erro no servidor*" ao fazer um pedido usando a publicação direta Authorize.Net.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Erro ao fazer pedido com a conta de sandbox Authorize.net (ocorreu um erro no servidor)

Este artigo fornece uma correção para &quot;*Erro no servidor*&quot;mensagem de erro ao fazer um pedido usando a Postagem direta do Authorize.Net.

>[!WARNING]
>
>**Aviso de desativação**
>
>Devido à Diretiva relativa aos serviços de pagamento [PSD 2](https://docs.magento.com/user-guide/v2.3/stores/compliance-payment-services-directive.html) e a evolução contínua de muitas APIs, a Authorize.Net corre o risco de se tornar desatualizada e não estar mais em conformidade com a segurança no futuro. Por esse motivo, ela agora está obsoleta, e recomendamos que você a desative na configuração do Adobe Commerce e faça a transição para a variável [extensão do Commerce Marketplace](https://marketplace.magento.com/extensions.html).
>
>**Essa integração foi removida da versão 2.4.0 do Adobe Commerce e foi descontinuada das versões atuais da 2.3.**
>
>Para obter detalhes sobre como fazer uma transição segura de integrações de pagamentos obsoletos, consulte nosso [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Problema

Fazer um pedido usando [Publicação direta no Authorize.Net](https://docs.magento.com/user-guide/v2.3/payment/authorize-net-direct-post.html) A conta de sandbox causa uma mensagem de erro:

>>
&quot;Erro no servidor. Tente fazer o pedido novamente&quot;

## Causa 1: o Modo de Teste está habilitado

Não parece óbvio, mas o Authorize.net&#39;s **Modo de teste** A configuração deve ser definida como **Não** mesmo ao testar com a conta de sandbox.

## Solução 1: desative o modo de teste

1. Ir para **Lojas** > **Configuração** > **Vendas** > **Métodos de pagamento** > **Outros métodos de pagamento** > **Publicação direta do Authorize.net**.
1. Definir **Modo de teste** para &quot;Não&quot; (desmarque **Usar valor do sistema** e, em seguida, selecione &quot;Não&quot; no menu).
1. Clique em **Salvar configuração**.

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Causa 2: URLs incorretos

As configurações do Authorize.net podem conter endereços de URL incorretos para os recursos críticos do Authorize.Net.

## Solução 2: forneça os URLs corretos

* **URL do gateway:**   `https://test.authorize.net/gateway/transact.dll`
* **URL de Detalhes da Transação:**   `https://apitest.authorize.net/xml/v1/request.api`
* **Referência da API:**   `https://developer.authorize.net/api/reference/`

## Se nada ajudou: obter informações de depuração

Se a inserção de um pedido com Authorize.net falhar com uma solicitação *&quot;Algo deu errado&quot;* erro, verifique o Adobe Commerce `debug.log`.

### Transact.dll

Caso a variável `debug.log` estiver vazio, marque a opção **transact.dll** resposta no console do navegador da web:

1. Abra o console.
1. Antes de fazer um pedido, acesse o **Rede** e selecione **Preservar log**.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Filtrar respostas por **transact.dll** para ver uma mensagem de resposta com um possível erro.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)

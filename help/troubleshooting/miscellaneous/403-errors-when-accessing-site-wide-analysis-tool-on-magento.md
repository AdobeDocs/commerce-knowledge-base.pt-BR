---
title: Erros 403 ao acessar a Ferramenta de análise do site no Adobe Commerce
description: Este artigo fornece uma solução para quando você recebe erros 403 ao tentar acessar a Ferramenta de análise do site no Adobe Commerce.
exl-id: f24fad17-62d6-4a0f-bcba-983c3dbee3d7
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Erros 403 ao acessar a Ferramenta de análise do site no Adobe Commerce

Este artigo fornece uma solução para quando você recebe erros 403 ao tentar acessar a Ferramenta de análise do site no Adobe Commerce.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.4.1 e posterior.

## Problema

Você recebe um erro 403 ao tentar acessar a Ferramenta de análise do site.

<u>Etapas a serem reproduzidas:</u>

Faça logon no painel de administração do Commerce e clique em **Relatórios** > *Insights do Sistema* > **Ferramenta de Análise do Site**.

<u>Resultado esperado:</u>

Você verá a Ferramenta de análise do site inteiro.

<u>Resultado real:</u>

Você vê: *Erro 403.*


## Solução

Para garantir que a Ferramenta de análise do site tenha o acesso adequado ao aplicativo, execute o comando a seguir na CLI. Substituir `<store URL>` pela URL de armazenamento:

```cURL
curl -sIL -X GET <store URL>/swat/key/index | grep HTTP
HTTP/2 403
```

Execute etapas dependendo do código de resposta obtido.

### 403 Código de resposta proibido

Se o código de resposta for 403, você pode ter a proteção de bot Cloudflare que está bloqueando a Ferramenta de análise do site. Para acessar a ferramenta, adicione seus IPs à lista de permissões:

* 107.23.33.174
* 3.225.9.244
* 3.88.83.85

### Corrija o código de resposta 200 e a saída JSON

Se a resposta for o código 200 correto e a saída JSON, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para escalonar o problema com o acesso à Ferramenta de Análise do Site.


### Código de resposta 500 (erro fatal)

Se um código de resposta for 500 (erro fatal), instale o patch MDVA-38526. Utilize um dos links a seguir para fazer download do patch, dependendo do tipo de patch desejado:

* Correção do Adobe Commerce na infraestrutura da nuvem: [MDVA-38526_EE_2.4.1-p1_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_v3.patch.zip)
* Patch do Adobe Commerce no Cloud Infrastructure Composer: [MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip)

O patch é aplicável ao Adobe Commerce na infraestrutura em nuvem versões 2.4.1 e posteriores.

### Resposta não JSON

Se a saída da resposta não for JSON, talvez seja devido à implementação de PWA/Headless. Se você estiver usando a implementação Headless, atualize a configuração UPWARD para ignorar as solicitações do Adobe Commerce Origin. Para fazer isso, no Administrador do Adobe Commerce, em **Lojas** > **Configuração** > **Geral** > **Web** > **Configuração de PWA ASCENDENTE** > **Inclui na lista de permissões de Nome principal**, adicione *swat*.

![Upward_configuration](assets/upward_pwa.png)

Se você ainda não conseguir acessar a Ferramenta de Análise do Site, ao fazer logon da próxima vez no painel de administração do Commerce e navegar até **Relatórios** > *Insights do Sistema* > **Ferramenta de Análise do Site**, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Leitura relacionada

* [Guia da Ferramenta de Análise do Site](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html)

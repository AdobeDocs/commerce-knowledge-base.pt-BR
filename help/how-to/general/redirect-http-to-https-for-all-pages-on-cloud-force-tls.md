---
title: Redirecionar HTTP para HTTPS para todas as páginas no Adobe Commerce na infraestrutura em nuvem (Forçar TLS)
description: Ative a funcionalidade **Forçar TLS** do Fastly no Administrador do Commerce para habilitar o redirecionamento global HTTP para HTTPS para todas as páginas do Adobe Commerce na loja de infraestrutura da nuvem.
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Redirecionar HTTP para HTTPS para todas as páginas no Adobe Commerce na infraestrutura em nuvem (Forçar TLS)

Ativar o Fastly **Forçar TLS** funcionalidade no Administrador da Commerce para habilitar o redirecionamento global de HTTP para HTTPS para todas as páginas da Adobe Commerce na loja de infraestrutura da nuvem.

Este artigo fornece informações [etapas](#steps), uma visão geral rápida do recurso Forçar TLS, versões afetadas e links para a documentação relacionada.

## Etapas {#steps}

### Etapa 1: configurar URLs seguros {#step-1-configure-secure-urls}

Nesta etapa, definimos os URLs seguros do armazenamento. Se isso já tiver sido feito, acesse [Etapa 2: Ativar Forçar TLS](#step-2-enable-force-tls).

1. Faça logon no Administrador do Commerce.
1. Navegue até **Lojas** > **Configuração** > **Geral** > **Web**.
1. Expanda a **URLs de base (Seguro)** seção.    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. No **URL de base segura** especifique o URL HTTPS do seu armazenamento.
1. Defina o **Usar URLs Seguros na Loja** e a variável **Usar URLs Seguros no Administrador** configurações para **Sim**.    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. Clique em **Salvar configuração** no canto superior direito para aplicar as alterações.

**Documentação relacionada em nosso guia do usuário:**   [Armazenar URLs](https://docs.magento.com/m2/ee/user_guide/stores/store-urls.html).

### Etapa 2: Ativar Forçar TLS {#step-2-enable-force-tls}

1. No Administrador do Commerce, navegue até **Lojas** > **Configuração** > **Avançado** > **Sistema**.
1. Expanda a **Cache de Página Inteira** seção, depois **Configuração do Fastly**, depois **Configuração avançada**.
1. Clique em **Forçar TLS** botão.    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. Na caixa de diálogo exibida, clique em **Carregar**.    ![magento-admin_force-tls-confirm-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. Após fechar a caixa de diálogo, verifique se o estado atual de Forçar TLS é exibido como **habilitado**.    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**Documentação relacionada do Fastly:**   [Forçar guia TLS](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md) para Adobe Commerce 2.

## Sobre o Force TLS

TLS (Transport Layer Security) é um protocolo para conexões HTTP seguras que substitui seu antecessor menos seguro — o protocolo SSL (Secure Socket Layer).

A funcionalidade Forçar TLS do Fastly permite forçar todas as solicitações não criptografadas recebidas para as páginas do site para o TLS.

>>
Funciona retornando um *301 Movido Permanentemente* resposta a qualquer solicitação não criptografada, que redireciona para o equivalente TLS. Por exemplo, fazer uma solicitação para *http://www.example.com/foo.jpeg* redirecionaria para *https://www.example.com/foo.jpeg*.

[Protegendo as comunicações](https://docs.fastly.com/guides/securing-communications/) (Documentação do Fastly)

## Versões afetadas

* **Adobe Commerce na infraestrutura em nuvem:**
   * versão: 2.1.4 e posterior
   * planos: Adobe Commerce na infraestrutura em nuvem Arquitetura do plano inicial e Adobe Commerce na infraestrutura em nuvem Arquitetura do plano Pro (incluindo Pro Legacy)
* **Fastly:** 1.2.4

## Nenhuma alteração necessária em route.yaml

Para ativar o redirecionamento de HTTP para HTTPS em **all** páginas da loja, não é necessário adicionar as páginas à `routes.yaml` arquivo de configuração — ativar Forçar TLS globalmente para toda a loja (usando o Commerce Admin) é suficiente.

## Documentação relacionada do Fastly

* [Forçar guia TLS para o Adobe Commerce 2](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [Forçar um redirecionamento TLS](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [Protegendo as comunicações](https://docs.fastly.com/guides/securing-communications/)

---
title: Bloqueadores iniciados no Adobe Commerce na infraestrutura em nuvem
description: Este artigo fornece uma correção para bloqueadores a serem iniciados no Adobe Commerce na infraestrutura em nuvem, incluindo problemas relacionados à configuração do Fastly, certificados SSL, redirecionamentos 301 e desempenho de ativos estáticos.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: df966df6a85057b26d53a870d038269ebdcc2b32
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---

# Bloqueadores iniciados no Adobe Commerce na infraestrutura em nuvem

Este artigo fornece uma correção para bloqueadores a serem iniciados no Adobe Commerce na infraestrutura em nuvem, incluindo problemas relacionados à configuração do Fastly, certificados SSL, redirecionamentos 301 e desempenho de ativos estáticos.

## 1. Configuração do Fastly

[Fastly](https://www.fastly.com/) é uma Rede de Entrega de Conteúdo (CDN) baseada em Verniz para veicular ativos estáticos. É necessário para o Adobe Commerce na infraestrutura em nuvem em ambientes de produção, portanto, é importante configurar o Fastly e testar seu site (UAT) com o Fastly ativado e configurado - nos ambientes de Preparo e Produção.

>[!WARNING]
>
>Com o Full Page Cache (FPC) habilitado, seu site funciona de forma diferente; certifique-se de testá-lo antes de entrar em funcionamento.

O processo de configuração do Fastly está documentado em detalhes no tópico [Configurar o Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=pt-BR) no guia do usuário. Abaixo estão as etapas importantes.

### 1-A. Verifique se você tem a versão mais recente do módulo Fastly instalada

Verifique se você tem a versão mais recente do módulo Fastly instalada para obter os recursos e as melhorias mais recentes. Para verificar se você tem a versão mais recente do Fastly, revise [Atualizar o módulo Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=pt-BR#upgrade-the-fastly-module) no nosso guia do usuário. Para obter mais detalhes, consulte [Configurar o Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=pt-BR) em nosso guia do usuário.

### 1-B. Ativar e configurar o Fastly usando o Commerce Admin

Para obter mais detalhes, consulte [Obter suas credenciais do Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=pt-BR#get-fastly-credentials) no guia do usuário.

### 1-C. Carregar trechos de VCL do Fastly

Para obter mais detalhes, consulte [Carregar VCL para Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=pt-BR) em nosso guia do usuário.

Você também pode [criar e adicionar seus próprios trechos de VCL personalizados](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=pt-BR).

### 1-D. Configurar DNS para o Fastly


Consulte este artigo para ver as etapas detalhadas: [Configurar o Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=pt-BR#update-dns-configuration-with-development-settings) em nosso guia do usuário.

### Artigos relacionados do Fastly em nossa base de conhecimento de suporte

* [O armazenamento em cache do Fastly não está funcionando na Nuvem](/help/troubleshooting/miscellaneous/fastly-caching-is-not-working-on-magento-cloud.md)
* [Erro ao limpar o cache do Fastly na Nuvem (A solicitação de limpeza não foi processada com êxito)](/help/troubleshooting/miscellaneous/error-purging-fastly-cache-on-cloud-the-purge-request-was-not-processed-successfully.md)

## 2. Certificado SSL (TLS) válido

Problema: Sem um certificado SSL válido e em funcionamento, não é possível testar métodos de pagamento externo na página Finalização da compra - no ambiente de Preparo.

Recomendação **:** Solicite seu certificado SSL compartilhado para nomes de domínio de preparo ou ativos.


## 3. Configurar e testar redirecionamentos 301

Problema: os redirecionamentos 301 não são fornecidos ou estão mal configurados, causando queda na sua loja em classificações de SEO e listas de pesquisa.

Recomendação **:** Configure e teste cuidadosamente os redirecionamentos 301.

Caso esteja migrando de um site antigo para um novo, os redirecionamentos do 301 fazem com que seus clientes acessem as páginas antigas indexadas anteriormente para as páginas apropriadas em sua nova loja, desta forma:

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Artigos relacionados:**

* [Redireciona por meio de route.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html?lang=pt-BR) em nosso guia do usuário.
* [Redireciona por meio do Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=pt-BR) em nosso guia do usuário.
* [Substituições de URL](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html?lang=pt-BR) em nosso guia do usuário.

## 4. Desempenho dos ativos

Problema: os ativos estáticos são fornecidos lentamente para que o site tenha um desempenho insatisfatório (tempo de carregamento longo, conteúdo multimídia não exibido etc.). Os ativos estáticos do seu site são recursos CSS, imagens, vídeos, documentos anexados e muito mais. A maneira como são organizados e atendidos é um fator importante no desempenho do site.

Recomendação: para identificar as possíveis causas de desempenho insatisfatório, considere usar o [Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) para testes de desempenho. Você também pode considerar estas ferramentas de terceiros:

* [Cerco](https://www.joedog.org/siege-home): utilitário de teste de carga e benchmarking HTTP; oferece suporte à autenticação básica, cookies, protocolos HTTP, HTTPS e FTP.
* [Jmeter](https://jmeter.apache.org/): uma ferramenta respeitável de teste de carga e medição de desempenho. Ajuda a medir o desempenho de tráfego pico, por exemplo, para vendas de flash.
* [New Relic](https://support.newrelic.com/): localiza processos e áreas do site que causam desempenho lento com o tempo rastreado gasto por ação, como dados de transmissão, consultas, Redis etc.
* [WebPageTest](https://www.webpagetest.org/) (gratuito) e [PKingdom](https://www.pingdom.com/) (pago): a análise em tempo real do tempo de carregamento das páginas do site com locais de origem diferentes.

Você também pode considerar a [minificação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=pt-BR) para CSS, JavaScript e HTML.

**Artigos relacionados:**

* [Testar implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html?lang=pt-BR) em nossa documentação de desenvolvedor.

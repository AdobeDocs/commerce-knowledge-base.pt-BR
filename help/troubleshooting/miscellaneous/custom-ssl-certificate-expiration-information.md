---
title: Informações de expiração do certificado SSL personalizado
description: Este artigo fornece uma solução para quando um certificado SSL personalizado foi atualizado com um certificado SSL fornecido pelo Adobe.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Informações de expiração do certificado SSL personalizado

Este artigo fornece uma solução para quando um certificado SSL personalizado foi atualizado com um certificado SSL fornecido pelo Adobe.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, [todas as versões compatíveis](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

O Adobe Commerce atualiza automaticamente os certificados SSL 30 dias antes da expiração. Essa automação não verifica se o certificado que está sendo substituído é um SSL interno ou um SSL de terceiros personalizado e o substituirá por um SSL interno válido após a detecção da expiração. Isso pode causar confusão para proprietários e operadores de sites que esperam ter o certificado personalizado no site, bem como o potencial para outros problemas de funcionalidade, incluindo, mas não limitado a, uma interrupção do site.

<u>Etapas a serem reproduzidas</u>

1. Certificado SSL personalizado instalado para o site.
1. A automação detecta que o certificado SSL personalizado está a 30 dias da expiração.
1. O Adobe Commerce substitui automaticamente o certificado personalizado pelo nosso certificado interno.

<u>Resultados esperados</u>

O Adobe Commerce ignora certificados personalizados ao executar a atualização automática do certificado SSL.

<u>Resultados reais</u>

O Adobe Commerce atualiza qualquer certificado quando ele está a 30 dias da expiração.

## Solução

Quando um comerciante opta por usar seu próprio certificado SSL personalizado, ele deve ser atualizado mais de 30 dias antes da expiração do certificado para garantir que não seja substituído por um certificado SSL interno da Adobe Commerce.

Se você estiver em uma situação em que seu SSL personalizado foi substituído pelo nosso SSL interno e deseja substituí-lo pelo seu certificado SSL personalizado atualizado, [enviar uma solicitação de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) com o local em que você fez upload dos novos arquivos de certificado. Inclua a data de início do novo SSL. Depois que tivermos essas informações, poderemos prosseguir com a instalação do novo certificado SSL.

## Leitura relacionada

* [Certificados SSL (TLS) para o Magento Commerce Cloud: Perguntas frequentes](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) em nossa base de conhecimento de suporte.
* [Referência de ferramentas de linha de comando: magento-cloud certificate:add](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-cloud.html#certificateadd) na documentação do desenvolvedor.
* [Lista de verificação de inicialização](https://devdocs.magento.com/cloud/live/site-launch-checklist.html)na documentação do desenvolvedor.
* [Ferramenta de análise do acesso em todo o site](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html#step-2-access-site-wide-analysis-tool) em nosso guia do usuário.

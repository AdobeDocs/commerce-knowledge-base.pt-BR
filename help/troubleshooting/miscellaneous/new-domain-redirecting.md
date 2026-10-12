---
title: O novo domínio está redirecionando para o domínio padrão
description: Este artigo fornece uma correção para o problema em que o novo domínio redireciona para o domínio padrão no ambiente existente ou diferente.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%
---
# O novo domínio está redirecionando para o domínio padrão

Este artigo fornece uma correção para o problema em que o novo domínio redireciona para o domínio padrão no ambiente existente ou diferente.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura do Cloud Pro (todas as versões)

## Problema

O novo domínio está redirecionando para o domínio padrão no ambiente atual ou para o domínio padrão de outro ambiente.

## Causa

Isso acontece quando as Variáveis não são atualizadas após a adição de um novo domínio ou quando o serviço [!DNL Fastly] errado é configurado no ambiente.

## Solução

1. Se o domínio estiver redirecionando no mesmo ambiente, verifique se você configurou as [Variáveis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables).
1. Se o domínio estiver redirecionando para outro ambiente, verifique se você configurou o serviço [!DNL Fastly] correto executando o seguinte comando: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>Você pode encontrar as credenciais da API [!DNL Fastly] fazendo logon em cada ambiente (Preparação/Produção) e verificando o arquivo `/mnt/shared/fastly_tokens.txt`. Para obter mais informações, consulte [configurar [!DNL Fastly] serviços](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) no Guia de Infraestrutura do Commerce na Nuvem.

Se ambas as configurações acima estiverem corretas, envie um tíquete de suporte.

## Leitura relacionada

* [Lista de verificação para configurar um novo domínio](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) em nossa knowledge base de suporte.

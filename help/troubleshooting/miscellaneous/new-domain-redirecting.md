---
title: O novo domínio está redirecionando para o domínio padrão
description: Este artigo fornece uma correção para o problema em que o novo domínio redireciona para o domínio padrão no ambiente existente ou diferente.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# O novo domínio está redirecionando para o domínio padrão

Este artigo fornece uma correção para o problema em que o novo domínio redireciona para o domínio padrão no ambiente existente ou diferente.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura do Cloud Pro (todas as versões)

## Problema

O novo domínio está redirecionando para o domínio padrão no ambiente atual ou para o domínio padrão de outro ambiente.

## Causa

Isso acontece quando as Variáveis não são atualizadas após adicionar um novo domínio ou a variável incorreta [!DNL Fastly] serviço foi configurado no ambiente.

## Solução

1. Se o domínio estiver redirecionando no mesmo ambiente, verifique se você configurou o [Variáveis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables).
1. Se o domínio estiver redirecionando para outro ambiente, verifique se você configurou o ambiente correto [!DNL Fastly] executando o seguinte comando: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>Você pode encontrar o [!DNL Fastly] Credenciais da API fazendo logon em cada ambiente (Preparo/Produção) e verificando o `/mnt/shared/fastly_tokens.txt` arquivo. Para obter mais informações, consulte [configurar [!DNL Fastly] serviços](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) no Guia de infraestrutura do Commerce na nuvem.

Se ambas as configurações acima estiverem corretas, envie um tíquete de suporte.

## Leitura relacionada

* [Lista de verificação para configurar um novo domínio](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) em nossa base de conhecimento de suporte.

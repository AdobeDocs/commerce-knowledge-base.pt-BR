---
title: Erro "Código de área não definido" ao executar setup:upgrade
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.3 relacionado ao erro *O código de área não está definido* ao executar o comando setup:upgrade.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%
---
# Erro &#39;Código de área não definido&#39; ao executar `setup:upgrade`

Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura de nuvem 2.2.3 relacionado à obtenção do erro *&quot;O código de área não está definido&quot;* ao executar o seguinte comando:

```bash
setup:upgrade
```

>[!NOTE]
>
>O problema foi corrigido no Adobe Commerce 2.2.4.

## Problema

Ao executar o

```bash
bin/magento setup:upgrade
```

, você receberá a seguinte mensagem de erro: *&quot;Module &#39;Magento\_AdvancedSalesRule&#39;: Installing data...Area code not set: Area code must be set before starting a session&quot;* and the command execution is stopped. O problema ocorre porque a configuração de área é solicitada antes de ser realmente definida. O patch permite capturar o erro e não interromper o processo de atualização.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.2.3

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.2.0 - 2.2.3

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) em nossa base de dados de conhecimento de suporte.

## Arquivos Anexados

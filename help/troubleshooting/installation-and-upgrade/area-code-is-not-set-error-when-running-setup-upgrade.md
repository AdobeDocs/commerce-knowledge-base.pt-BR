---
title: Erro "Código de área não definido" ao executar setup:upgrade"
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.3 relacionado ao erro *O código de área não está definido* ao executar o comando setup:upgrade.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 4617b915a62093e00da428a753d913a39d30f3a0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Erro &quot;Código de área não definido&quot; ao executar `setup:upgrade`

Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.3 relacionado à obtenção do *&quot;Código de área não definido&quot;* erro ao executar o seguinte comando:

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

, você receberá a seguinte mensagem de erro: *&quot;Módulo &#39;Magento\_AdvancedSalesRule&#39;: instalando dados...Código de área não definido: O código de área deve ser definido antes de iniciar uma sessão&quot;* e a execução do comando é interrompida. O problema ocorre porque a configuração de área é solicitada antes de ser realmente definida. O patch permite capturar o erro e não interromper o processo de atualização.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.2.3

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.2.0 - 2.2.3

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de conhecimento de suporte.

## Arquivos Anexados

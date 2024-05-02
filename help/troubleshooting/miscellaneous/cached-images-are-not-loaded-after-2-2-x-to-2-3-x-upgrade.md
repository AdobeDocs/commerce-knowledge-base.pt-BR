---
title: As imagens em cache não são carregadas após a atualização do 2.2.X para o 2.3.X
description: Este artigo fornece a solução para o problema de imagens em cache que não são exibidas após a atualização do Adobe Commerce na infraestrutura em nuvem 2.2.X para 2.3.X.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# As imagens em cache não são carregadas após a atualização do 2.2.X para o 2.3.X

Este artigo fornece a solução para o problema de imagens em cache que não são exibidas após a atualização do Adobe Commerce na infraestrutura em nuvem 2.2.X para 2.3.X.

## Versões e edições afetadas:

* Adobe Commerce na infraestrutura em nuvem Arquitetura de plano Pro 2.2.X, 2.3.X

## Problema

Depois que o Adobe Commerce é atualizado de 2.2.X para 2.3.X, as imagens do produto em cache não ficam disponíveis e uma página 404 é exibida.

O problema é causado pela configuração incorreta do Nginx definida no `.magento.app.yaml`: `index.php` (ou nenhum) é usado para o `"/media"` localização em vez de `passthru: /get.php`.

## Solução

1. Verifique o seu `.magento.app.yaml` arquivo de configuração, no campo `"/media"` localização. A configuração correta é semelhante à seguinte:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Se `passthru` não está definido como `"/get.php"` e `expires` não estiver definido, siga as etapas abaixo.
1. Corrija o arquivo de configuração.
   * Starter Plan: corrija o arquivo por conta própria e envie as alterações.
   * Plano Pro:
   * Integração: corrija o arquivo por conta própria e envie as alterações.
   * Preparo e produção: corrija o arquivo sozinho, envie as alterações para e crie um [tíquete de suporte do Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para ser aplicado.

1. Ative a otimização de imagem do Fastly no Administrador do Commerce (O Fastly deve ser configurado anteriormente), conforme descrito em <https://devdocs.magento.com/guides/v2.3/cloud/cdn/fastly-image-optimization.html>.

Se a configuração estiver correta, mas o problema persistir, continue a investigação ou entre em contato com [Suporte ao Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

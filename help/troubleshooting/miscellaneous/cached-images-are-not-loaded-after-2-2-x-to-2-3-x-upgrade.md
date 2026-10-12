---
title: As imagens em cache não são carregadas após a atualização do 2.2.X para o 2.3.X
description: Este artigo fornece a solução para o problema de imagens em cache que não são exibidas após a atualização do Adobe Commerce na infraestrutura em nuvem 2.2.X para 2.3.X.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%
---
# As imagens em cache não são carregadas após a atualização do 2.2.X para o 2.3.X

Este artigo fornece a solução para o problema de imagens em cache que não são exibidas após a atualização do Adobe Commerce na infraestrutura em nuvem 2.2.X para 2.3.X.

## Versões e edições afetadas:

* Adobe Commerce na infraestrutura em nuvem Arquitetura de plano Pro 2.2.X, 2.3.X

## Problema

Depois que o Adobe Commerce é atualizado de 2.2.X para 2.3.X, as imagens do produto em cache não ficam disponíveis e uma página 404 é exibida.

O problema é causado pelo conjunto incorreto de configuração Nginx em `.magento.app.yaml`: `index.php` (ou nenhum) é usado para o local `"/media"` em vez de `passthru: /get.php`.

## Solução

1. Verifique o arquivo de configuração `.magento.app.yaml` no local `"/media"`. A configuração correta é semelhante à seguinte:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Se `passthru` não estiver definido como `"/get.php"` e `expires` não estiver definido, siga estas etapas.
1. Corrija o arquivo de configuração.
   * Starter Plan: corrija o arquivo por conta própria e envie as alterações.
   * Plano Pro:
   * Integração: corrija o arquivo por conta própria e envie as alterações.
   * Preparo e produção: corrija o arquivo você mesmo, envie as alterações por push e crie um [tíquete de suporte do Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) para aplicá-lo.

1. Habilite a otimização de imagem do Fastly no Administrador do Commerce (O Fastly deve ser configurado previamente), conforme descrito em <https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization>.

Se a configuração estiver correta, mas o problema persistir, continue a investigação ou contate o [Suporte da Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).

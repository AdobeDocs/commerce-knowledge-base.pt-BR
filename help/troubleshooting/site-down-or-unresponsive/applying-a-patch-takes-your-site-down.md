---
title: A aplicação de um patch derruba o site
description: Este artigo fala sobre o problema em que um patch que você acabou de aplicar derruba seu site. Para resolvê-lo, você pode remover o patch.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '289'
ht-degree: 0%
---
# A aplicação de um patch derruba o site

Este artigo fala sobre o problema em que um patch que você acabou de aplicar derruba seu site. Para resolvê-lo, você pode remover o patch.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação), todas as versões compatíveis
* Magento Open Source, todas as versões

## Problema

Depois de aplicar um patch, seu site fica inativo.

## Causa

Esse problema pode ocorrer devido a uma incompatibilidade de versão entre o patch que você acabou de aplicar ao seu site, suas personalizações, outros patches que você aplicou no passado ou algum outro erro.

## Solução

Remova o patch. O método de remoção de patch é diferente para o Adobe Commerce na infraestrutura em nuvem do que para o Adobe Commerce no local e o Magento Open Source.

### Magento Open Source, todas as versões 1.X

Para versões do Magento Open Source 1.X,

* Execute o seguinte comando SSH: `h SUPEE_patch --revert `

### Adobe Commerce no local, Magento Open Source, todas as versões 2.x

Para versões do Adobe Commerce no local e Magento Open Source 2.x,

1. Execute o seguinte comando SSH:

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   (Se o comando acima não funcionar, tente usar `-p2` em vez de `-p1`)

1. Para que as alterações sejam refletidas, atualize o cache no Administrador em **Sistema** > **Gerenciamento de Cache**.

### Adobe Commerce na infraestrutura em nuvem, todas as versões

Para o Adobe Commerce na infraestrutura em nuvem, todas as versões,

1. Remova o(s) arquivo(s) `%patch_name%.composer.patch` do diretório `m2-hotfixes`.
1. Confirme e envie por push as alterações de código:

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Leitura relacionada

* [Como aplicar uma correção de compositor fornecida pelo Adobe](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) em nossa base de dados de conhecimento de suporte.

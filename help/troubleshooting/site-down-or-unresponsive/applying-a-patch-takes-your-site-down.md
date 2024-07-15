---
title: A aplicação de um patch derruba o site
description: Este artigo fala sobre o problema em que um patch que você acabou de aplicar derruba seu site. Para resolvê-lo, você pode remover o patch.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
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

Para versões Adobe Commerce no local e Magento Open Source 2.x,

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

* [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.

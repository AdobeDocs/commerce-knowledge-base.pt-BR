---
title: Como aplicar um patch de compositor fornecido pelo Adobe
description: Este artigo instrui como aplicar um patch de compositor para Adobe Commerce no local, Adobe Commerce na infraestrutura em nuvem e Magento Open Source.
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Como aplicar um patch de compositor fornecido pelo Adobe

Este artigo instrui como aplicar um patch de compositor para Adobe Commerce no local, Adobe Commerce na infraestrutura em nuvem e Magento Open Source.

>[!WARNING]
>
>É altamente recomendável aplicar e testar o patch no ambiente de Preparo/Integração antes de aplicá-lo à Produção. Também recomendamos que você tenha um backup recente antes de qualquer manipulação.

## Como aplicar um patch compositor para Adobe Commerce na infraestrutura em nuvem {#cloud}

1. Se você não tiver um diretório chamado `m2-hotfixes` na raiz do projeto, crie uma.
1. Copie o `%patch_name%.composer.patch` arquivo(s) para o `m2-hotfixes` diretório.
1. Adicionar, confirmar e enviar por push suas alterações de código:

   ```git
   git add -A
   ```

   ```git
   git commit -m "Apply %patch_name%.composer.patch patch"
   ```

   ```git
   git push origin
   ```

Para obter informações adicionais sobre como aplicar patches a projetos na nuvem, consulte [Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

### Como aplicar um patch do compositor para Adobe Commerce no local e Magento Open Source {#commerce}

1. Carregue o patch no seu diretório Adobe Commerce local ou no diretório raiz de Magento Open Source.
1. Execute o seguinte comando SSH:

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   (Se o comando acima não funcionar, tente usar `-p2` em vez de `-p1` )

1. Para que as alterações sejam refletidas, atualize o cache no Administrador em **Sistema** > **Gerenciamento de cache**.

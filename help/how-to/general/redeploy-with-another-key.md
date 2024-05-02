---
title: "Adobe Commerce na nuvem: altere as chaves de autenticação e reimplante"
description: Este artigo fornece instruções sobre como reimplantar o Adobe Commerce na infraestrutura em nuvem com chaves de autenticação diferentes. Por exemplo, você pode ter usado as chaves de outra conta ou pode ter usado chaves Magento Open Source em vez de chaves Adobe Commerce.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce na nuvem: altere as chaves de autenticação e reimplante

Este artigo fornece instruções sobre como reimplantar o Adobe Commerce na infraestrutura em nuvem com chaves de autenticação diferentes. Por exemplo, você pode ter usado as chaves de outra conta ou pode ter usado chaves Magento Open Source em vez de chaves Adobe Commerce.

Se você tiver usado as chaves incorretas, a implantação falhará. Para recuperar, você deve clonar o projeto, adicionar as chaves corretas para `auth.json`e enviará a alteração para a ramificação mestre.

Neste artigo, pressupomos que seu projeto tenha uma `master` somente ramificação (`master` é a ramificação padrão ao criar um projeto pela primeira vez).

Para reimplantar com as chaves de autenticação corretas:

1. Faça logon no computador que tem suas chaves SSH do Adobe Commerce na infraestrutura em nuvem.
1. Faça logon no projeto:

   ```
   magento-cloud login
   ```

1. Criar uma ramificação para atualizar o código com o nome `auth`:

   ```
   magento-cloud environment:branch auth master
   ```

1. Mude para o diretório raiz do projeto.
1. Abertura `auth.json` em um editor de texto.

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Adicione as chaves de autenticação corretas.
1. Salve as alterações e saia do editor de texto.
1. Confirme e mescle suas alterações.

   ```
   git add -A
   ```

   ```
   git commit -m "<description of change>"
   ```

   ```
   git push origin master
   ```

1. Aguarde a conclusão da implantação.

As mensagens indicam se a implantação foi bem-sucedida. É possível confirmar uma implantação bem-sucedida acessando um dos **Rotas de ambiente** exibido na tela.

---
title: Resolver problemas com a chave de criptografia
description: Este artigo fala sobre como corrigir os problemas causados por a chave de criptografia não ser movida junto com o despejo de banco de dados para outro ambiente.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: 0458b37e2af4c9ad2ec92a1fdd6844ef222ef84a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Resolver problemas com a chave de criptografia

Este artigo fala sobre como corrigir os problemas causados por a chave de criptografia não ser movida junto com o despejo de banco de dados para outro ambiente.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.x

## Problema

Depois de importar um [despejo de banco de dados](/help/how-to/general/create-database-dump-on-cloud.md) dos ambientes de Produção para os de Preparo/Integração, os números de cartão de crédito salvos parecem incorretos e/ou os pagamentos falham para integrações de pagamento que exigem o uso de credenciais de comerciante.

## Causa

A chave de criptografia usada para criptografar dados confidenciais, como números de cartão de crédito e credenciais de comerciantes, não é armazenada no banco de dados e, portanto, não é transferida para outro ambiente após a importação/exportação de despejo do banco de dados.

## Solução

Você precisa copiar a chave de criptografia do ambiente de origem e adicioná-la ao ambiente de destino.

Para copiar a chave de criptografia:

1. O SSH para o projeto que foi a origem do despejo do banco de dados, conforme descrito em [SSH para o ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=pt-BR) na documentação do desenvolvedor.
1. Abra `app/etc/env.php` em um editor de texto.
1. Copie o valor de `key` para `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

Para definir o valor da chave para o projeto de destino:

1. Abra o [Cloud Console](https://console.adobecommerce.com) e localize o projeto.
1. Defina o valor da variável [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=pt-BR) (na documentação do desenvolvedor), conforme descrito em [Configurar o projeto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=pt-BR) na documentação do desenvolvedor. Isso disparará o processo de implantação e `CRYPT_KEY` será substituído no arquivo `app/etc/env.php` em cada implantação.

Como opção, você pode substituir manualmente a chave de criptografia no arquivo `app/etc/env.php`:

1. SSH para o ambiente de destino.
1. Abra `app/etc/env.php` em um editor de texto.
1. Cole os dados copiados como o valor `key` para `crypt`.
1. Salve o `env.php` editado.
1. Limpe o cache no ambiente de destino executando o `bin/magento cache:clean` ou no Administrador do Commerce em **Sistema** > **Ferramentas** > **Gerenciamento de Cache**.

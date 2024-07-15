---
title: Redefine o erro de desserialização "setup:static-content:deploy"
description: Este artigo fornece uma correção para o erro de desserialização do Redis ao executar `magento setup:static-content:deploy`.
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Erro de desserialização de Redis `setup:static-content:deploy`

Este artigo fornece uma correção para o erro de desserialização Redis ao executar `magento setup:static-content:deploy`.

A execução de `magento setup:static-content:deploy` causa o erro Redis:

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

O problema é causado por processos de interferência paralela na conexão Redis.

Para resolver, execute `setup:static-content:deploy` em um modo de thread único definindo a seguinte variável de ambiente:

```
STATIC_CONTENT_THREADS =1
```

ou execute o comando `setup:static-content:deploy` seguido pelo argumento `-j 1` (ou `--jobs=1` ).

Observe que a desativação do multithreading retarda o processo de implantação de ativos estáticos.

## Versões afetadas

* Adobe Commerce no local: 2.1.2 e posterior
* Adobe Commerce na infraestrutura em nuvem 2.1.2 e posterior
* Redis, qualquer versão

## Problema

A execução do comando `setup:static-content:deploy` causa o erro Redis:

```php
)
[2017-06-02 19:57:59] Command:php ./bin/magento setup:static-content:deploy --jobs=3  en_US

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[CredisException]
read error on connection

[RedisException]
read error on connection

.....

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[RuntimeException]
Command php ./bin/magento setup:static-content:deploy --jobs=3  en_US  returned code 3
```

## Causa

O problema é causado por processos de interferência paralela na conexão Redis.

Aqui, um processo em `App/Config/Type/System.php` esperava uma resposta para `system_defaultweb`, mas recebeu uma resposta para `system_cache_exists` que foi feita por um processo diferente. Veja a explicação detalhada na [publicação de Jason Woods](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Solução

Desabilite o paralelismo e execute `setup:static-content:deploy` em um modo de thread único definindo a seguinte variável de ambiente:

```
STATIC_CONTENT_THREADS =1
```

Você também pode executar o comando `setup:static-content:deploy` seguido pelo argumento `-j 1` (ou `--jobs=1`).

>[!NOTE]
>
>No modo de segmento único, o processo de implantação de conteúdo estático pode levar quatro vezes mais tempo.

## Mais informações

Em nossa documentação do desenvolvedor:

* [Configurar Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [Atualização de linha de comando](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)

---
title: Erros de implantação ao confirmar arquivos incorretos
description: Este artigo fornece uma solução para o problema que ocorre quando você recebe erros de implantação causados por confirmações incorretas no repositório de arquivos/pastas que não deveriam ter sido adicionados.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Erros de implantação ao confirmar arquivos incorretos

Este artigo fornece uma correção para o problema que ocorria ao receber erros de implantação causados por confirmações incorretas no repositório de arquivos/pastas que não deveriam ter sido adicionados.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

Você está recebendo erros de implantação ao confirmar no repositório de arquivos/pastas. Por exemplo, o seguinte erro é causado devido a uma tentativa de conexão com o BD quando ele não está disponível durante a [Fase de Compilação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#build-phase):

```SQL
SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          PDO::__construct(): php_network_getaddresses: getaddrinfo for database.inte  
          rnal failed: Name or service not known       
```

## Causa

Determinados arquivos/pastas não devem ser confirmados no repositório, pois causam uma quebra no [fluxo de trabalho de implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html).

## Solução

Remova esses arquivos/pastas do repositório se eles estiverem presentes:

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`

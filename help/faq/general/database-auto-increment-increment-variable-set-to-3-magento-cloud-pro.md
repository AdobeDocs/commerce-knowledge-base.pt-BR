---
title: Variável de incremento de auto_incremento do banco de dados definida como "3" Adobe Commerce em nossa arquitetura Cloud Pro
description: Esse é o comportamento esperado para as soluções de arquitetura de plano Pro da infraestrutura em nuvem do Adobe Commerce devido à arquitetura de 3 nós e não pode ser modificado.
exl-id: ea478cbc-2dc2-41c9-8ea7-7e2f308e5948
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Variável de incremento de auto_incremento do banco de dados definida como &quot;3&quot; Adobe Commerce em nossa arquitetura Cloud Pro

Esse é o comportamento esperado para as soluções de arquitetura de plano Pro da infraestrutura em nuvem do Adobe Commerce devido à arquitetura de 3 nós e não pode ser modificado.

O cluster de banco de dados Galera é usado, que é um cluster de banco de dados com um banco de dados MariaDB MySQL por nó com uma configuração de incremento automático de três para IDs exclusivas em cada banco de dados.

<u>Por que a ID de incremento usada em clusters Pro nem sempre é separada/incrementada por 3?</u>

A ID de incremento usada em clusters nem sempre é separada/incrementada por 3 devido ao modo como o Galera funciona.

Cada um dos três servidores gerencia seu próprio espaço de ID, e o incremento que está sendo usado depende de qual é o servidor de banco de dados principal do MySQL (dependendo da carga relativa) - daí as lacunas variáveis.
Se você usar SSH para cada nó e se conectar à instância do MySQL local em execução nesse nó usando a porta 3307 (em vez de usar proxy para o &quot;principal&quot; na porta padrão 3306), verá a seguinte figura:

![auto_increment](assets/auto_increment_id.png)

Por exemplo, se o principal selecionado for o nó 1, em que `auto_increment_offset = 1`, a ID seria incrementada em 1. Em seguida, se um novo nó principal for selecionado posteriormente, por exemplo, nó 3, em que `auto_increment_offset = 3`, ele seria incrementado em 3.

## Links úteis

Consulte na documentação do desenvolvedor:

* [Nuvem para Adobe Commerce > Arquitetura Pro > Backup e recuperação de desastres](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [Cloud para Adobe Commerce > Instalar pré-requisitos: banco de dados](https://devdocs.magento.com/cloud/before/before-workspace-magento-prereqs.html#database)

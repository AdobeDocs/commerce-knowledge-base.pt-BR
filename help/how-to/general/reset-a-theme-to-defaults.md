---
title: Redefinir um tema para os padrões
description: Dependendo de problemas que você possa encontrar ao personalizar seus temas e desenvolver sua loja, talvez não tenha acesso por meio do Administrador do Commerce. Você pode limpar e redefinir para o padrão do tema sem acessar o Administrador. Depois de limpar o tema, o tema Luma padrão será aplicado.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Redefinir um tema para os padrões

Dependendo de problemas que você possa encontrar ao personalizar seus temas e desenvolver sua loja, talvez não tenha acesso por meio do Administrador do Commerce. Você pode limpar e redefinir para o padrão do tema sem acessar o Administrador. Depois de limpar o tema, o tema Luma padrão será aplicado.

Ao desenvolver componentes Adobe Commerce (todas as implantações) e Magento Open Source (módulos, temas e pacotes de idiomas), seu ambiente em rápida mudança requer que você limpe periodicamente determinados diretórios e caches. Caso contrário, o código será executado com exceções e não funcionará corretamente. Para obter detalhes, consulte [Limpar diretórios durante o desenvolvimento](https://developer.adobe.com/commerce/php/development/components/clear-directories/) na documentação do desenvolvedor.

## Ambiente e tecnologias

* Adobe Commerce no local
* Adobe Commerce na infraestrutura em nuvem
* Magento Open Source

## Pré-requisitos

* Ferramentas de banco de dados

## Etapas

Se você precisar redefinir o tema de armazenamento, mas não puder acessar o painel Admin, poderá redefini-lo no banco de dados fazendo o seguinte:

1. Use uma ferramenta de banco de dados como [phpMyAdmin](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou acesse o BD manualmente a partir da linha de comando para executar a seguinte consulta SQL: `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Limpe os seguintes diretórios:
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

Dessa forma, não haverá um tema definido no nível de exibição da loja e, quando você recarregar as páginas iniciais da loja, o tema Luma padrão será aplicado.

## Informações adicionais

* [Limpar diretórios durante o desenvolvimento](https://developer.adobe.com/commerce/php/development/components/clear-directories/) em nossa documentação do desenvolvedor

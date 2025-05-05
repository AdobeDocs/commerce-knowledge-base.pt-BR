---
title: Após a instalação, as imagens e folhas de estilos não são carregadas; somente o texto é exibido, sem gráficos
description: Este artigo descreve os possíveis motivos e soluções para o problema em que as folhas de estilos e imagens não são carregadas após a instalação do Adobe Commerce.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Após a instalação, as imagens e folhas de estilos não são carregadas; somente o texto é exibido, sem gráficos

Este artigo descreve os possíveis motivos e soluções para o problema em que as folhas de estilos e imagens não são carregadas após a instalação do Adobe Commerce.

## Produtos e versões afetados

* Adobe Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problema

<u>Etapas a serem reproduzidas</u>

1. Instale o Adobe Commerce.
1. Navegue até a vitrine ou o Administrador.

<u>Resultado esperado</u>

Os estilos são aplicados, nenhum elemento da interface do usuário parece ter estilos ausentes.

<u>Resultado real</u>

Os estilos não são aplicados corretamente, gráficos estão ausentes.

## Causa

O caminho para imagens e folhas de estilos não está correto, devido a um URL base incorreto ou porque as regravações do servidor (CentOS, Ubuntu) não estão configuradas corretamente.

Para confirmar esse é o caso, use um inspetor de navegador da Web para verificar os caminhos para ativos estáticos e se esses ativos estão localizados no sistema de arquivos Adobe Commerce ou Magento Open Source.

Os ativos estáticos estão localizados em `<magento_root>/pub/static/` , nos diretórios `frontend` e `adminhtml`.

## Solução

As soluções possíveis a seguir dependem do software usado e da causa do problema:

* Se você estiver usando o servidor Web Apache, verifique sua configuração [regravações do servidor](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/web-server/apache#apache-rewrites-and-htaccess) e a URL base do servidor Adobe Commerce/Magento Open Source e tente novamente. Se você configurar a diretiva `AllowOverride` do Apache incorretamente, os arquivos estáticos não serão enviados do local correto.
* Se você estiver usando o servidor Web nginx, certifique-se de [configurar um arquivo de host virtual](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/web-server/nginx). O arquivo de host virtual nginx deve atender aos seguintes critérios:
   * A diretiva `include` deve apontar para a amostra do arquivo de configuração nginx no diretório de instalação do Adobe Commerce/Magento Open Source. Por exemplo:    `include /var/www/html/magento2/nginx.conf.sample;`
   * A diretiva `server_name` deve corresponder à URL de base especificada ao instalar o Adobe Commerce/Magento Open Source. Por exemplo: `server_name 192.186.33.10;`
* Se o aplicativo estiver no [modo de produção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/setup/application-modes#production-mode), tente implantar arquivos de exibição estáticos usando o comando `magento setup:static-content:deploy`. Para obter detalhes sobre a implantação de arquivos estáticos, consulte [Implantar arquivos de exibição estáticos](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) na documentação do desenvolvedor.

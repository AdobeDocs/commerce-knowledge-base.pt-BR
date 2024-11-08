---
title: Erro de versão do PHP ou erro 404 ao acessar o Adobe Commerce no navegador
description: Este artigo fornece soluções para os problemas em que você não pode acessar sua instância do Adobe Commerce em um navegador da Web e receber o erro 404 ou o erro "versão PHP não suportada".
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Erro de versão do PHP ou erro 404 ao acessar o Adobe Commerce no navegador

Este artigo fornece soluções para os problemas em que você não pode acessar sua instância do Adobe Commerce em um navegador da Web e receber o erro 404 ou o erro &quot;versão PHP não suportada&quot;.

## Produtos e versões afetados:

* Adobe Commerce 2.3.x

## Problema: versão PHP não suportada

A seguinte mensagem é exibida quando você tenta acessar a loja da Adobe Commerce ou o administrador da Commerce:

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### Solução

Tente o seguinte:

* Atualize o PHP para a versão 7.3. Para obter mais informações, consulte [requisitos da pilha de tecnologia do Adobe Commerce 2.3](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements) na documentação do desenvolvedor.
* Reinicie o Apache, já que ele pode não estar usando a mesma versão do PHP que está no sistema de arquivos. Para reiniciar o Apache, use os seguintes comandos:
   * Ubuntu: `service apache2 restart`
   * CentOS: `service httpd restart`

## Problema: erro 404

Um erro 404 (Não encontrado) é exibido ao tentar acessar a loja da Adobe Commerce ou o administrador do Commerce.

### Solução

Tente o seguinte:

* Verifique se as [regravações do Apache Server](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/web-server/apache) estão habilitadas. Se as regravações do servidor Apache estiverem definidas incorretamente, os arquivos estáticos não serão enviados do local correto.
* Pode haver um problema com o URL de base inserido durante a instalação. Você especifica a URL de base como o valor de `--base-url=` ao instalar o Adobe Commerce a partir da linha de comando ou como o valor do campo **Seu endereço de armazenamento** na página Configuração da Web do instalador da Web. A URL base *deve* começar com o esquema (como `http://` ) e terminar com uma barra à direita (/). Execute o instalador novamente com um valor válido e tente acessar o Adobe Commerce depois disso.

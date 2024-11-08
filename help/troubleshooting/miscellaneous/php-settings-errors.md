---
title: Erros de configurações de PHP
description: Este artigo fornece soluções para erros de configuração do PHP.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Erros de configurações de PHP

Este artigo fornece soluções para erros de configuração do PHP.

## Erro de limite de memória do PHP

As verificações de prontidão garantem que você tenha pelo menos 1GB de memória reservada para processos PHP. Essa configuração deve ser suficiente para a maioria das instalações, incluindo a instalação de dados de amostra opcionais. No entanto, recomendamos pelo menos 2 GB para depuração.

Para aumentar o limite de memória do PHP:

1. Faça logon no servidor do Adobe Commerce.
1. Localize o arquivo `php.ini` usando este comando:

   ```
   bash    $ php --ini
   ```

1. Como um usuário com privilégios `root`, use um editor de texto para abrir o `php.ini` especificado por `Loaded Configuration File`.
1. Localizar `memory_limit`.
1. Altere para um valor de `2GB` para uso e depuração normais.
1. Salve as alterações em `php.ini` e saia do editor de texto.
1. Reinicie o servidor Web. Exemplos a seguir:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (CentOS e Ubuntu): `service nginx restart`

1. Tente instalar novamente.

## erro max-input-vars devido a formulários grandes

Configurações com um alto número de lojas, produtos, atributos ou opções podem gerar formulários que excedem o limite predefinido do PHP. Se o número de valores enviados ultrapassar o limite `max-input-vars` definido em `php.ini` (o padrão é 1000), os dados restantes não serão transferidos e esses valores do banco de dados não serão atualizados. Quando isso ocorre, um aviso é exibido no log do PHP:

```bash
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Não há valor &#39;apropriado&#39; para `max-input-vars`; isso depende do tamanho e da complexidade da sua configuração. Modifique o valor no arquivo `php.ini` conforme necessário. Consulte [Configurações PHP necessárias](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings).

## erro de nível de aninhamento de função máxima xdebug

Consulte [Durante a instalação, erro de nível máximo de aninhamento de função xdebug](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Os erros são exibidos ao acessar um modelo PHTML

Normalmente, o texto de erro é:

```bash
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Solução: Defina `asp_tags = off` em php.ini

Vários modelos têm sintaxe para suporte de nível abstrato em modelos (use diferentes mecanismos de modelos, como o Twig) envolvidos em `<% %>` tags, como este [modelo](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) para exibir uma imagem de produto:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Mais informações sobre [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Editar `php.ini` e definir `asp_tags = off`. Para obter mais informações, consulte [Configurações PHP necessárias](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings).

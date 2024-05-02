---
title: Mensagem de erro ao adicionar sites à Verificação de segurança
description: Este artigo fornece soluções possíveis para o problema quando um usuário não consegue adicionar sites à [Verificação de segurança da Commerce](https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Mensagem de erro ao adicionar sites à Verificação de segurança

Este artigo fornece soluções possíveis para o problema de quando um usuário não consegue adicionar sites à [Verificação de segurança do Commerce](https://account.magento.com/scanner/dashboard/).

## Produtos e versões afetados

* Adobe Commerce (todos os métodos e versões de implantação)
* Magento Open Source

## Problema

O usuário não pode adicionar sites à [Verificação de segurança do Commerce](https://account.magento.com/scanner/dashboard/). A seguinte mensagem de erro é exibida ao tentar adicionar um site: *Não é possível enviar o site para varredura.*

## Solução

1. Verifique se os seguintes endereços IP não estão bloqueados nas portas 80 e 443:
   * 52.87.98.44
   * 34 196 167 176
   * 3.218.25.102

1. O código de confirmação diferencia tempo. Se tiverem decorrido mais de 30 minutos após a notificação **Adicionar site** foi clicado, o código provavelmente expirou.
1. Não se esqueça de limpar o cache e garantir que o código de validação apareça no corpo de origem da página inicial. O código de confirmação deve ser inserido de acordo com as especificações de marcação HTML: o comentário HTML pode ser inserido no corpo da página (sugerimos colocá-lo na seção de rodapé); a tag META deve estar somente na seção de cabeçalho.
1. Antes de clicar em **Verificar código de confirmação**, abra o console de desenvolvedor do navegador, clique no link **Rede** e verifique a resposta de magento.com. Ele deve ser HTTP 200 (OK) e o corpo da resposta deve conter um objeto JSON.
1. Se o código de resposta for HTTP 200 e o corpo de resposta for um objeto JSON e a variável `verified` o valor da propriedade é `false`, significa que o código não foi encontrado na página. A variável `details` o valor da propriedade deve conter a explicação. Por exemplo, se o armazenamento usar um certificado SSL autoassinado, provavelmente haverá um erro de conexão.

Se ainda não conseguir adicionar sites, conclua as seguintes etapas:

1. Coloque outro comentário HTML na página:

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. Envie um tíquete de suporte e forneça as seguintes informações:
   * URL de loja da Adobe Commerce
   * MAGEID + email da conta Magento.com
   * Nome + Sobrenome
   * Nome da empresa
   * Lista de emails de notificação separados por vírgulas

## Leitura relacionada

* [Verificação de segurança](https://docs.magento.com/user-guide/magento/security-scan.html) em nosso guia do usuário.

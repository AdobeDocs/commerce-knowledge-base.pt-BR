---
title: Solução de problemas de erro 503 causados pela necessidade de alterar as configurações padrão de Verniz
description: Este artigo fornece soluções para solucionar problemas de erro 503 causados por determinados valores padrão de Cache de verniz que não são suficientes para sua loja.
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 9c5e993b69a98865a1142110625252da848eae04
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Solução de problemas de erro 503 causados pela necessidade de alterar as configurações padrão de Verniz

Este artigo fornece soluções para solucionar problemas de erro 503 causados por determinados valores padrão de Cache de verniz que não são suficientes para sua loja.

## Problema

Se o comprimento das tags de cache usadas pelo Adobe Commerce exceder o padrão de 8192 bytes do Varnish, você poderá ver erros HTTP 503 (falha na busca do back-end) no navegador. Os erros podem ser exibidos de modo semelhante ao seguinte: *&quot;Erro 503 Falha na busca do back-end. Falha na busca do back-end&quot;*

## Solução

Para resolver esse problema, aumente o valor padrão do `http_resp_hdr_len` no arquivo de configuração do Vernish. A variável `http_resp_hdr_len` parâmetro especifica o tamanho máximo do cabeçalho *no prazo de* o tamanho total de resposta padrão de 32.768 bytes.

>[!NOTE]
>
>Se a variável `http_resp_hdr_len` exceder 32K, você também deverá aumentar o tamanho de resposta padrão usando o `http_resp_size` parâmetro.

1. Como usuário com `root` abra o arquivo de configuração do Vanish em um editor de texto:
   * CentOS 6: `/etc/sysconfig/varnish`
   * CentOS 7: `/etc/varnish/varnish.params`
   * Debian: `/etc/default/varnish`
   * Ubuntu: `/etc/default/varnish`
1. Procure por `http_resp_hdr_len` parâmetro.
1. Se o parâmetro não existir, adicione-o depois de `thread_pool_max` .
1. Definir `http_resp_hdr_len` para um valor igual à contagem de produtos da maior categoria multiplicada por 21. (Cada tag do produto tem aproximadamente 21 caracteres.)    Por exemplo, definir o valor para 65536 bytes deve funcionar se sua maior categoria tiver 3.000 produtos.    Por exemplo:    ```conf    -p http_resp_hdr_len=65536 \    ```
1. Defina o `http_resp_size` para um valor que acomode o comprimento aumentado do cabeçalho de resposta.    Por exemplo, usar a soma do comprimento do cabeçalho aumentado e do tamanho de resposta padrão é um bom ponto de partida (por exemplo, 65536 + 32768 = 98304): `-p http_resp_size=98304`. Segue um trecho:

   ```
   # DAEMON_OPTS is used by the init script.
   DAEMON_OPTS="-a ${VARNISH_LISTEN_ADDRESS}:${VARNISH_LISTEN_PORT} \
       -f ${VARNISH_VCL_CONF} \
       -T ${VARNISH_ADMIN_LISTEN_ADDRESS}:${VARNISH_ADMIN_LISTEN_PORT} \
       -p thread_pool_min=${VARNISH_MIN_THREADS} \
       -p thread_pool_max=${VARNISH_MAX_THREADS} \
       -p http_resp_hdr_len=65536 \
       -p http_resp_size=98304 \
       -p workspace_backend=98304 \
       -S ${VARNISH_SECRET_FILE} \
       -s ${VARNISH_STORAGE}" \
   ```

## Tempos limite de verificação de integridade {#health-check-timeouts}

Se você desativar o cache enquanto o Vernish estiver configurado como o aplicativo de cache e enquanto o Adobe Commerce estiver no modo de desenvolvedor, pode ser impossível fazer logon no Administrador.

Essa situação pode ocorrer porque a verificação de integridade padrão tem um `timeout` de 2 segundos. Pode levar mais de 2 segundos para que a verificação de integridade colete e mescle informações sobre cada solicitação de verificação de integridade. Se isso ocorrer em 6 de 10 verificações de integridade, o servidor do Adobe Commerce será considerado não íntegro. O verniz serve conteúdo obsoleto quando o servidor não está íntegro.

Como o Administrador é acessado pelo Varnish, você não pode fazer logon no Administrador para ativar o armazenamento em cache (a menos que o Adobe Commerce se torne íntegro novamente). No entanto, você pode usar o seguinte comando para habilitar o cache:

```bash
$ bin/magento cache:enable
```

Para obter mais informações sobre o uso da linha de comando, consulte [Introdução à configuração da linha de comando](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands.html).

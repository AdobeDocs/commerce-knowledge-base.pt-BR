---
title: "Falha na implantação na liberação de cache: não há comandos definidos no erro de namespace 'cache'"
description: Este artigo fornece uma solução para o problema de falha na implantação com o seguinte erro **Não há comandos definidos no namespace do cache**.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: e13be3ef9daa17b9463c8251933f68f6a35fedd2
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Falha na implantação na liberação de cache: &quot;Não há comandos definidos no erro de namespace &#39;cache&#39;&quot;

>[!WARNING]
>
>Faça backup do banco de dados primeiro, se estiver fazendo isso em um site de produção ativo, antes de executar essas etapas.

Este artigo fornece uma solução para o problema que ocorre quando a implantação falha e um dos erros no log tem esta aparência:

```
[YEAR-DAYTIME] ERROR: [127] The command "php ./bin/magento cache:flush --ansi --no-interaction" failed.
        There are no commands defined in the "cache" namespace.
...
      W:     There are no commands defined in the "cache" namespace.
```

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.4.x

## Problema  

<u>Etapas a serem reproduzidas</u>:

Tentativa de implantação. 

<u>Resultados esperados</u>:

Implantação bem-sucedida.

<u>Resultados reais</u>:

Você não implantou o com sucesso. Nos logs, você vê um erro de implantação com uma mensagem semelhante à seguinte *Não há comandos no namespace de cache*.

### Causa

A tabela **core_config_data** contém configurações para uma ID de armazenamento ou ID de site que não existe mais no banco de dados. Isso ocorre quando você importa um backup de banco de dados de outra instância/ambiente e as configurações desses escopos permanecem no banco de dados por meio do(s) armazenamento(s)/site(s) associado(s) que foi(ram) excluído(s).

### Solução

Se você tiver apenas um site, o segundo teste dos sites não se aplica e você só precisa testar as lojas.

Para resolver esse problema, identifique as linhas inválidas restantes dessas configurações.

1. Adicione SSH ao servidor e execute este comando:

   `bin/magento`

1. A mensagem de erro pode indicar quais linhas e tabelas permanecem no banco de dados a partir de sites excluídos. Por exemplo, um erro indica que o armazenamento solicitado não foi encontrado:

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. Execute esta consulta MySql para verificar se o armazenamento não pode ser encontrado, o que é indicado pela mensagem de erro na etapa 2. 

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Execute a seguinte instrução MySql para excluir as linhas inválidas: 

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store); 
   ```

1. Execute este comando novamente:

   `bin/magento`

   Se você receber um erro como o abaixo, que indica que o site com a ID X solicitada não foi encontrado, você tem configurações restantes        no banco de dados a partir de site(s) e armazenamento(s) que foram excluídos.

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   Execute esta consulta MySql e verifique se o site não pode ser encontrado:

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Execute esta instrução MySql para excluir as linhas inválidas da configuração do site:

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

Para confirmar se a solução funcionou, execute o comando `bin/magento` novamente. Você não deve mais ver os erros e pode implantar com êxito.

## Leitura relacionada

* [Solução de problemas de implantação do Adobe Commerce](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html)
* [Verificação do log de implantação se a interface do usuário da nuvem tiver um erro de &quot;log recortado&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)

---
title: 'Falha na implantação na liberação de cache: ''Não há comandos definidos no erro ''cache'' namespace'''
description: Este artigo fornece uma solução para o problema de falha na implantação com o seguinte erro **Não há comandos definidos no namespace do cache**.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# Falha na implantação na liberação de cache: erro &quot;Não há comandos definidos no namespace &#39;cache&#39;&quot;

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

A tabela **`core_config_data`** contém configurações para uma ID de loja ou ID de site que não existe mais no banco de dados. Isso ocorre quando você importa um backup de banco de dados de outra instância/ambiente e as configurações desses escopos permanecem no banco de dados por meio do(s) armazenamento(s)/site(s) associado(s) que foi(ram) excluído(s).

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

1. Execute esta consulta [!DNL MySQL] para verificar se o armazenamento não foi encontrado, o que é indicado pela mensagem de erro na etapa 2.

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Execute a seguinte instrução [!DNL MySQL] para excluir as linhas inválidas:

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

   Execute esta consulta [!DNL MySQL] e verifique se o site não pode ser encontrado:

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Execute esta instrução [!DNL MySQL] para excluir as linhas inválidas da configuração do site:

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

Para confirmar se a solução funcionou, execute o comando `bin/magento` novamente. Você não deve mais ver os erros e pode implantar com êxito.

## Leitura relacionada

* [Solução de problemas de implantação do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter)
* [Verificando o log de implantação se a Interface de Usuário da Nuvem tem o erro &quot;log cortado&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

---
title: '[!DNL MySQL] espaço em disco insuficiente no Adobe Commerce na infraestrutura em nuvem'
description: Este artigo fornece soluções para quando você está tendo muito pouco espaço ou sem espaço para  [!DNL MySQL] no Adobe Commerce na infraestrutura em nuvem. Os sintomas podem incluir paralisações do site, clientes que não conseguem adicionar produtos ao carrinho, não conseguem se conectar ao banco de dados, acessar o banco de dados remotamente e não conseguem aplicar SSH ao nó. Os sintomas também incluem o Galera, sincronização de ambiente, PHP, banco de dados e erros de implantação, conforme listado abaixo. Clique em [Solução](https://support.magento.com/hc/en-us/articles/360058472572#solution) para ir diretamente para a seção de solução.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 660c463850abc145a22c34174aff45ac5ede6707
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 0%

---

# [!DNL MySQL] espaço em disco insuficiente no Adobe Commerce na infraestrutura em nuvem

Este artigo fornece soluções para quando você está tendo muito pouco espaço ou sem espaço para [!DNL MySQL] no Adobe Commerce na infraestrutura em nuvem. Os sintomas incluem paralisações do site, clientes que não conseguem adicionar produtos ao carrinho, não conseguem se conectar ao banco de dados, acessar o banco de dados remotamente e não conseguem aplicar SSH ao nó. Os sintomas também incluem o Galera, sincronização de ambiente, PHP, banco de dados e erros de implantação, conforme listado abaixo. Clique em [Solução](https://support.magento.com/hc/en-us/articles/360058472572#solution) para ir diretamente para a seção de solução.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Problema

O banco de dados fica muito grande. Os sintomas podem incluir perda da conexão do banco de dados, erro de upload do banco de dados e uma variedade de outros problemas.

Erros que você pode encontrar:

Galera:

* *SQLSTATE\[08S01\]: Falha de link de comunicação: o WSREP 1047 ainda não preparou o nó para uso do aplicativo*   *Erros de importação:*
* *SQLSTATE\[HY000\]: Erro geral: 1180 Erro 5 &quot;Erro de entrada/saída&quot;*
* *SQLSTATE\[08S01\]: Falha de link de comunicação: o WSREP 1047 ainda não preparou o nó para uso do aplicativo*

Erros de sincronização de ambiente:

* *SQLSTATE: Erro geral: 1180 Recebeu o erro 5 &quot;Erro de entrada/saída&quot; durante a CONFIRMAÇÃO*

Erros de PHP:

* *php: PDO::\_\_construct(): [!DNL MySQL] o servidor desapareceu.*
* *erros php: PDO::\_\_construct(): erro ao ler pacote de saudação. PID=NNNN.*
* *ERRO 2013 (HY000): Conexão perdida com o servidor [!DNL MySQL] em &#39;lendo pacote de comunicação inicial&#39;, erro do sistema: 0 &quot;Erro interno/verificação (Não é erro do sistema)&quot;.*

Erros de banco de dados:

* *Erro\_código: 1114*
* *InnoDB: Erro (espaço em disco insuficiente) ao gravar o nó do word na tabela de índice auxiliar FTS.*
* *SQLSTATE\[HY000\]: Erro geral: 2006 [!DNL MySQL] o servidor desapareceu*
* *\[ERROR\] SQL Escravo: Erro &#39;A tabela `<table\_name>` está cheia&#39; na consulta.*
* *A unidade mysql.service entrou em estado de falha.*
* *erro: &#39;Não é possível conectar ao servidor [!DNL MySQL] local por meio do soquete &#39;/var/run/mysqld/mysqld.sock&#39; (111 &quot;Conexão recusada&quot;)&#39;*
* *1205 Tempo limite de espera de bloqueio excedido; tente reiniciar a transação; a consulta era: INSERT INTO \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`scheduled\_at\`) VALUES (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Erros de implantação:

* *E: O comando &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; retornou um status de saída diferente de zero 255*
* *E: Comando &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 reiniciar site-`<environment name>`g-nginx&#39;\]&#39; retornou diferente de zero*
* *Atualizando esquema.. SQLSTATE\[HY000\]: Erro geral: 1114 A tabela `<table\_name>` está cheia*
* *SQLSTATE\[HY000\]: Erro geral: 3 Erro ao gravar arquivo ./`<environment name>`/\#*
* *W: `<filename>` (Errcode: 28 &quot;Não há espaço disponível no dispositivo&quot;)* *Erros de indexação (juntamente com arquivos .ibd temporários órfãos em /tmp):*
* *O indexador de Regra de Catálogo gera uma exceção. As tabelas temporárias não são limpas na sequência e, em seguida, preenchem o disco no nó mestre [!DNL MySQL] atual*

<u>Etapas a serem reproduzidas</u>:

Uma das maneiras de verificar se o `/data/mysql` (ou onde quer que o armazenamento de dados do [!DNL MySQL] esteja configurado) está cheio é executando o seguinte comando na CLI:

```bash
df -h
```

Menos de 10% da memória livre no disco [!DNL MySQL] é um indicador primário de uma interrupção.

## Causa

A montagem `/data/mysql` pode ficar cheia devido a vários problemas, como não ter inodes suficientes, espaço de armazenamento disponível e consultas incorretas que geram tabelas temporárias.

## Solução

Você pode dar um passo imediato para colocar [!DNL MySQL] de volta no caminho certo (ou evitar que ele fique preso): libere espaço liberando mesas grandes.

Mas uma solução de longo prazo seria alocar mais espaço e seguir as [práticas recomendadas do Banco de Dados](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=pt-BR), incluindo a habilitação da funcionalidade [Arquivo de Pedidos/Faturas/Remessas](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

Veja a seguir detalhes sobre soluções rápidas e de longo prazo.

### Verificar e liberar inodes

Verifique se há inodes disponíveis suficientes. Para fazer isso, execute o seguinte comando:

```bash
df -i
```

A saída seria semelhante ao seguinte:

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Verifique se o % de uso é &lt;70%. Os nós estão correlacionados com os arquivos. Se você remover arquivos da partição, liberará inodes.

### Verificar e liberar espaço de armazenamento

Verifique o espaço de armazenamento disponível. Para isso, execute:

```bash
df -k
```

A saída seria semelhante ao seguinte:

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

Se o % de uso for >70%, você precisará tomar medidas para liberar/adicionar algum espaço.

### Verificar arquivos `ibtmp1` grandes

Verifique se há um arquivo grande `ibtmp1` em `/data/mysql` de cada nó: esse arquivo é o tablespace para tabelas temporárias. Se houver consultas incorretas que geram tabelas temporárias, elas estarão contidas no arquivo `ibtmp1`. Este arquivo só é removido quando o banco de dados é reiniciado. Se estiver ocupando todo o espaço disponível, o banco de dados deverá ser reiniciado. Se houver consultas incorretas, elas serão recriadas novamente.

### Liberar tabelas grandes

>[!WARNING]
>
>É altamente recomendável criar um backup de banco de dados antes de executar qualquer manipulação e evitá-la durante períodos de carregamento de site alto. Consulte [Despejar seu banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) na documentação do desenvolvedor.

Verifique se há tabelas grandes e considere se alguma delas pode ser liberada. Faça isso no nó principal (origem).

Por exemplo, as tabelas com relatórios geralmente podem ser liberadas. Para obter detalhes sobre como localizar tabelas grandes, consulte o artigo [Localizar tabelas grandes [!DNL MySQL] 2&rbrace;.](/help/how-to/general/find-large-mysql-tables.md)

Se não houver tabelas de relatório enormes, considere liberar `_index` tabelas, apenas para retornar o aplicativo Adobe Commerce de volta ao controle. `index_price` tabelas seriam os melhores candidatos. Por exemplo, `catalog_category_product_index_storeX` tabelas, em que X pode ter valores de &quot;1&quot; até a contagem máxima de armazenamento. Lembre-se de que você precisaria reindexar para restaurar dados nessas tabelas e, no caso de catálogos grandes, esse reindexação pode levar muito tempo.

Depois de liberá-los, aguarde a conclusão da sincronização wsrep. Agora você pode criar backups e executar etapas mais relevantes para adicionar mais espaço, como alocar/comprar mais espaço e habilitar a funcionalidade de [arquivamento de Pedidos/Faturas/Remessas](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

### Verificar configurações de log binário

Verifique as configurações de log binário do servidor [!DNL MySQL]: `log_bin` e `log_bin_index`. Se as configurações estiverem ativadas, os arquivos de log poderão se tornar enormes. [Criar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando a limpeza de arquivos de log binários grandes. Além disso, solicite a verificação de que o registro binário está sendo configurado corretamente para que os registros sejam removidos periodicamente e não ocupem muito espaço.

Se você não tiver acesso às configurações do servidor [!DNL MySQL], solicite suporte para verificá-las.

### Recuperar espaço em disco alocado não utilizado

1. SSH no nó um e logon no MySQL:

   ```sh
   mysql -h127.0.0.1 -p`php -r "echo (include('app/etc/env.php'))['db']['connection']['default']['password'];"` -u`whoami` `whoami`
   ```

   Para obter etapas detalhadas, consulte [Conectar e executar consultas no banco de dados do Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-learn/tutorials/backend-development/remote-db-connection-execute-queries).

1. Verificar se há espaço não utilizado:

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) AS size_MB, round((data_free)/1048576,2) AS Allocated_but_unused FROM information_schema.tables WHERE data_free > 1048576*10 ORDER BY data_free DESC;
   ```


   Exemplo de saída:

   | table_name | size_MB | Allocated_but_unused |
   |----------------------|----------|--------------------------|
   | sales_order_grid | 28145,20 | 14943,00 |


   Verifique na saída se há memória alocada, mas não usada. Isso ocorre quando os dados foram excluídos de uma tabela, no entanto, a memória ainda está alocada para essa tabela.


1. Coloque o site no modo de manutenção e pare os trabalhos do cron para que não haja interações ocorrendo no banco de dados. Para obter etapas, consulte [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) e [Desabilitar trabalhos cron](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs).
1. Recupere esse espaço recriando a tabela com o seguinte comando (exemplo usando a tabela listada acima com o espaço mais não utilizado):

   ```sql
   ALTER TABLE sales_order_grid Engine = "INNODB";
   ```

1. Execute a consulta a seguir para verificar o espaço não alocado para cada tabela que mostra um valor alto na coluna **[!UICONTROL Allocated_but_unused]**.

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) as size_MB, round((data_free)/1048576,2) as Allocated_but_unused FROM information_schema.tables WHERE 1 AND data_free > 1048576*10 ORDER BY 
   data_free DESC;
   ```


1. Agora [Desabilite o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#enable-or-disable-maintenance-mode-1) e [Habilite os trabalhos cron](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs).


### Alocar/comprar mais espaço

Aloque mais espaço em disco para [!DNL MySQL] se você tiver algum espaço não utilizado. Consulte o artigo [Verificar limite de espaço em disco](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) para saber como verificar se há espaço livre em disco.

* Para os ambientes Starter plan, all ambientes e Pro plan Integration, é possível alocar o espaço em disco se você tiver algum não utilizado. Para obter detalhes, consulte [Alocar mais espaço para [!DNL MySQL]](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* Para ambientes de Preparo e Produção do plano Pro, [entre em contato com o suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para alocar mais espaço em disco se você tiver algum espaço não utilizado.

Se você tiver atingido o limite de espaço e ainda enfrentar problemas de pouco espaço, considere comprar mais espaço em disco, entre em contato com a equipe de conta da Adobe para obter detalhes.

## Leitura relacionada

[Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

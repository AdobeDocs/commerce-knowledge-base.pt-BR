---
title: Atualização do MariaDB 10.4 para 10.5 para Adobe Commerce na nuvem
description: O MariaDB 10.4 encerra o suporte em 18 de junho de 2024. Este artigo explica como atualizar o MariaDB da versão 10.4 para 10.5 para continuar usando o Adobe Commerce na infraestrutura em nuvem.
feature: Best Practices, Cloud
exl-id: 065840b8-28c1-4686-95fc-df3e73152845
source-git-commit: 11f2fae3264a61413c5da1b93ef4980151a1df1e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Atualização do MariaDB 10.4 para 10.5 para Adobe Commerce na nuvem

MariaDB é um banco de dados empresarial de código aberto usado com o Adobe Commerce.

O MariaDB 10.4 chegará ao fim do suporte em [18 de junho de 2024](https://endoflife.date/mariadb). Você não está mais em conformidade com PCI quando está em uma versão não suportada do MariaDB. Este artigo explica como atualizar do MariaDB 10.4 para 10.5 para continuar usando o Adobe Commerce na infraestrutura em nuvem.

>[!NOTE]
>
>À medida que o MariaDB 10.4 atingir o fim da vida útil (EOL), ele não será mais compatível com as versões atuais do Adobe Commerce. A prática recomendada é remover qualquer versão de EOL dentro de 30 dias do EOL.

## Produto e versões afetados

* Todos os Adobe Commerce no local e na infraestrutura em nuvem 2.4.4 e 2.4.5

## Solução

Adote os novos patches somente de segurança (2.4.4-p9 ou 2.4.5-p8) que serão lançados em 11 de junho de 2024 para garantir a compatibilidade com o MariaDB 10.5. Em seguida, siga as etapas abaixo para atualizar do MariaDB 10.4 para 10.5.

### Etapas de atualização para implantações em nuvem

1. Crie um [backup de BD usando os comandos de backup ECE-Tools DB](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Esse backup deve ser feito antes das etapas 2 e 3, caso algo dê errado ao atualizar tabelas/linhas.
1. [Verificar e converter todas as tabelas compactas em tabelas dinâmicas](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). Essa etapa é necessária para evitar uma possível perda de dados durante a atualização do banco de dados.
1. Verifique se há tabelas MYISAM. Você precisa [converter todas as tabelas MyISAM em InnoD](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. Depois de preparar as tabelas e linhas do banco de dados (as duas etapas anteriores), crie um backup do [BD usando os comandos de backup ECE-Tools DB](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Abra um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para agendar a atualização do MariaDB 10.4 para 10.5. No ticket, detalhe a data e hora em que deseja atualizar o BD. A equipe de suporte precisa de um aviso de 48 horas e a equipe de desenvolvimento do comerciante precisa estar disponível. Quando a hora e a data forem acordadas para a atualização, faça o seguinte:
   1. Coloque seu site no modo de manutenção e pare qualquer atividade de BD, por exemplo, crons.
   1. Crie um [backup de BD usando os comandos de backup ECE-Tools DB](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Informe ao suporte que você concluiu o backup por meio do tíquete de suporte. Para obter etapas para visualizar e rastrear seus tíquetes, consulte o [Guia do Usuário da Central de Ajuda da Adobe Commerce: Rastreie seus Tíquetes](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) em nossa base de conhecimento de suporte.
   1. A equipe de suporte do Adobe Commerce inicia o processo de atualização do MariaDB. Se todas as etapas acima tiverem sido executadas e o banco de dados for do tamanho médio, o processo levará cerca de uma hora. Bancos de dados maiores demoram mais. Quando a atualização estiver concluída, você será informado pelo seu ticket.
1. Desabilitar modo de manutenção. Consulte [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) na documentação do desenvolvedor.

>[!NOTE]
>
>É recomendável criar um backup de BD antes e depois de cada etapa de atualização para eliminar qualquer possibilidade de perda de dados. Isso permitirá a reversão para uma etapa anterior se surgirem problemas em qualquer momento durante a atualização da versão.

## Leitura relacionada

* [Guia de práticas recomendadas de atualização do BD](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites) para implantações locais.
* [Atualize o MariaDB 10.0 para 10.2 para Adobe Commerce na nuvem](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) em nossa base de dados de conhecimento de suporte.
* [política de ciclo de vida do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) na documentação do desenvolvedor.

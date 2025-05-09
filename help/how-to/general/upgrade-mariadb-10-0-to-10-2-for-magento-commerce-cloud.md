---
title: Atualização do MariaDB 10.0 para 10.2 para Adobe Commerce na nuvem
description: O MariaDB 10.0 e 10.1 estão no fim da vida útil (EOL). [O suporte terminou em 31 de março de 2019 e 17 de outubro de 2020, respectivamente](https://endoflife.date/mariadb). Este artigo explica como atualizar o MariaDB de 10.0 para 10.2 ou 10.2 para 10.3 ou para 10.4, para usar o Adobe Commerce na infraestrutura em nuvem.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Atualização do MariaDB 10.0 para 10.2 para Adobe Commerce na nuvem

O MariaDB 10.0 e 10.1 estão no fim da vida útil (EOL). [O suporte terminou em 31 de março de 2019 e 17 de outubro de 2020, respectivamente](https://endoflife.date/mariadb). Este artigo explica como atualizar o MariaDB de 10.0 para 10.2 ou 10.2 para 10.3 ou para 10.4, para usar o Adobe Commerce na infraestrutura em nuvem.

>[!NOTE]
>
>O MariaDB 10.0 é EOL (fim da vida útil) e não é compatível com as versões atuais do Adobe Commerce. A prática recomendada é remover qualquer versão de EOL dentro de 30 dias do EOL.

## Produto e versões afetados

* O MariaDB 10.2 é recomendado para o Adobe Commerce na infraestrutura em nuvem 2.3.x.
* MariaDB 10.4 é recomendado para 2.4.x. O MariaDB 10.3 também é compatível com o Adobe Commerce na infraestrutura em nuvem 2.4.x.

## Etapas de atualização

Para atualizar do MariaDB 10.0 para 10.2 ou 10.2 para 10.3 ou para 10.4, conclua as seguintes etapas:

1. Crie um [backup de BD usando os comandos de backup ECE-Tools DB](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Isso deve ser feito antes das etapas 2 e 3, caso algo dê errado ao atualizar tabelas/linhas.
1. [Verificar e converter todas as tabelas compactas em tabelas dinâmicas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html?lang=pt-BR). Isso é necessário para evitar uma possível perda de dados durante a atualização do banco de dados.
1. Verifique se há tabelas MYISAM. Você precisa [converter todas as tabelas MyISAM em InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=pt-BR).
1. Depois de preparar as tabelas e linhas do banco de dados (as duas etapas anteriores), crie um backup do [BD usando os comandos de backup ECE-Tools DB](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Abra um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para agendar a atualização do MariaDB 10.0 para 10.2 ou 10.2 para 10.3 ou 10.4. Nos detalhes do tíquete, especifique a data e a hora em que deseja atualizar o BD. A equipe de suporte precisa de um aviso de 48 horas e a equipe de desenvolvimento dos comerciantes precisa estar disponível. Quando a hora e a data forem acordadas para a atualização, faça o seguinte:
   1. Coloque seu site no modo de manutenção e pare qualquer atividade de BD, por exemplo, crons.
   1. Crie um [backup de BD usando os comandos de backup ECE-Tools DB](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Informe ao suporte que você concluiu o backup. Faça isso por meio do tíquete de suporte. Para obter etapas para visualizar e rastrear seus tíquetes, consulte o [Guia do Usuário da Central de Ajuda da Adobe Commerce: Rastreie seus Tíquetes](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) em nossa base de conhecimento de suporte.
   1. A equipe de suporte do Adobe Commerce iniciará o processo de atualização do MariaDB. Se todas as etapas acima tiverem sido executadas e o banco de dados for do tamanho médio, isso poderá ser feito em cerca de uma hora. Bancos de dados maiores levarão mais tempo. Você será informado por meio do tíquete assim que a atualização for concluída.
1. Desabilitar modo de manutenção. Consulte [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre os requisitos do Adobe Commerce 2.4.x, consulte [Requisitos do sistema do Adobe Commerce 2.4 > Banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/system-requirements#database) em nossa documentação para desenvolvedores.

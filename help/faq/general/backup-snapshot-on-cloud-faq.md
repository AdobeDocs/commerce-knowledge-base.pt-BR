---
title: 'Backup (instantâneo) na nuvem: Perguntas frequentes'
description: Este artigo aborda os conceitos básicos para fazer backup de seus ambientes com snapshots no Adobe Commerce na infraestrutura em nuvem.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 3df2d07bb5765fb0ddcb4417b7c4e4ae33ef2d42
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 0%

---

# Backup (instantâneo) na nuvem: Perguntas frequentes

Este artigo aborda o backup de seus ambientes com instantâneos no Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.x
* Planos de arquitetura: Starter, Pro Legacy, Pro

## Instantâneo do ambiente, plano Pro

### Ambientes de preparo e produção

* Os instantâneos manuais não estão disponíveis para ambientes de preparo e produção no plano Pro.
* Instantâneos automáticos são criados **independentemente do estado ativo** do site (instantâneos também são criados para sites que ainda não foram inicializados). Os backups automáticos não são acessíveis publicamente, pois são armazenados em um sistema separado.
Você pode [enviar um tíquete de Suporte da Adobe Commerce](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para solicitar um backup especial ou restaurar de um backup específico fornecendo a data, a hora e o fuso horário no tíquete. Depois que a equipe de infraestrutura tiver fornecido o instantâneo, para determinar o carimbo de data e hora quando ele foi originalmente tirado, execute o seguinte comando no local onde o instantâneo foi colocado:

  `cat /mnt/recovery/vol-<volume_id>/snap.time`

  Exemplo de saída:

  <strong>1-01-2025-13 08:42:17.123000+00:00</strong>


* O suporte não gera instantâneos manuais sob demanda. Além disso, observe que o suporte não executa a reversão ou restauração do banco de dados para você - eles recuperam o instantâneo, mas você mesmo deve restaurar o banco de dados.
* Instantâneos automáticos são criados **independentemente do estado ativo** do site (instantâneos também são criados para sites que ainda não foram inicializados). Os backups automáticos são armazenados em um sistema separado e não estão acessíveis ao público.
Você pode [enviar um tíquete de Suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md) para solicitar um backup especial ou restaurar de um backup específico fornecendo a data, a hora e o fuso horário no tíquete. O suporte não gera instantâneos manuais sob demanda.
Além disso, observe que o suporte não executa a reversão ou restauração do banco de dados para você - eles recuperam o instantâneo, mas você mesmo deve restaurar o banco de dados.
* Os backups são criados usando os **instantâneos criptografados do Amazon Web Services Elastic Block Store (AWS EBS)**.
* Os snapshots do ambiente incluem o sistema completo (sistema de arquivos e banco de dados).
* O tempo de retenção para instantâneos automáticos **é diferente** e segue [o agendamento](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery).

>[!NOTE]
>
>O Console da Nuvem sempre mostra [!UICONTROL No backup] em ambientes de Preparo e Produção. Só é possível fazer backups do ambiente de integração. Selecione **[!UICONTROL Backup]** no menu suspenso de reticências.
>
>![cloud_console_backup.png](assets/cloud_console_backup.png)

### Ambiente de integração (desenvolvimento)

* O backup do seu [ambiente de integração](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) **não é automático**, mas você pode criar instantâneos **manualmente**.
* Você pode criar snapshots manuais para ambientes de Integração em lojas sem transmissão ao vivo.
* Você pode ter **vários instantâneos** que foram acionados manualmente.
* Um instantâneo disparado manualmente é armazenado por **7 dias**.

**Artigos relacionados em nossa documentação para desenvolvedores:**

* [Backup e recuperação de desastres](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [Criar um instantâneo](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/snapshots)

## Instantâneo do ambiente, plano inicial

* Todos os tipos de ambientes (Integração, Preparo, Produção) **não estão sendo incluídos no backup automaticamente**, mas você pode criar instantâneos manualmente.
* Você pode criar instantâneos manuais **independentemente do estado ativo** do site (instantâneos também criados para sites que ainda não foram inicializados).
* Um instantâneo disparado manualmente é armazenado por **7 dias**.

## Restaurar um instantâneo do ambiente

Para restaurar um instantâneo existente (no ambiente compatível: Integração, Preparo, Produção no plano Starter ou Integração no plano Pro), siga as etapas em [Gerenciamento de backup: Restaurar um backup manual](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) em nosso Guia de Infraestrutura do Commerce na Nuvem.

## Backup do banco de dados (BD)

O backup de BD faz parte de um instantâneo da nuvem:

Um instantâneo é um backup completo de um ambiente que inclui todos os dados persistentes de todos os serviços em execução (por exemplo, **seu banco de dados MySQL**, Redis e assim por diante) e quaisquer arquivos armazenados nos volumes montados.

>[!NOTE]
>
>Os volumes montados incluem/referem-se apenas a [montagens graváveis](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/properties#mounts) e não incluirão todo o diretório `/app`. Quanto aos outros arquivos, eles são criados/gerados pelo [processo de compilação e implantação](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow), e você também terá que fazer check-out dos arquivos restantes do seu repositório Git.

[Gerenciamento de instantâneos e backup](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/snapshots) em nossa documentação do desenvolvedor.

Envie apenas uma [solicitação de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md) para um instantâneo do banco de dados de produção e preparo profissionais se precisar do banco de dados a partir de um momento específico. Se você precisar de um backup atual apenas do seu banco de dados (em qualquer ambiente), consulte o artigo da base de dados de conhecimento: [Gerar despejos de banco de dados na Nuvem](/help/how-to/general/create-database-dump-on-cloud.md).

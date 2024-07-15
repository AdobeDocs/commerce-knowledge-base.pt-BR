---
title: Vários trabalhos cron agendados para o mesmo período de tempo
description: Este artigo fornece uma correção para um problema conhecido do Adobe Commerce 2.2.2 relacionado à programação de vários trabalhos cron para execução ao mesmo tempo após a edição das variáveis de tempo para determinadas tarefas no administrador do Commerce.
exl-id: a3c1fe77-ed4c-43b5-8d6f-e5c549096c73
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Vários trabalhos cron agendados para o mesmo período de tempo

Este artigo fornece uma correção para um problema conhecido do Adobe Commerce 2.2.2 relacionado à programação de vários trabalhos cron para execução ao mesmo tempo após a edição das variáveis de tempo para determinadas tarefas no administrador do Commerce.

## Problema

Quando o cron está configurado para execução a cada minuto, se você editar variáveis de tempo para três tarefas agendadas no Admin, a tabela de banco de dados `cron_schedule` mostrará grupos de várias tarefas agendadas para execução ao mesmo tempo.

<u>Etapas a serem reproduzidas</u>:

1. Na Administração do Commerce, navegue até **Lojas** > Configurações > **Configuração** > **AVANÇADO** > **Sistema** > **Cron (Tarefas Agendadas)** > **Opções de configuração do Cron para o grupo: padrão.**
1. Configure as seguintes opções:
   * **Limpeza de Histórico a Cada**: desmarque a caixa de seleção **Usar sistema** e defina como *1440*.
   * **Vida Útil do Histórico de Êxito**: desmarque a caixa de seleção **Usar sistema** e defina como *1440*.
   * **Duração do Histórico de Falhas**: desmarque a caixa de seleção **Usar sistema** e defina como *1440*.

1. Clique em **Salvar configuração**.
1. No SSH, execute o comando `crontab -e`.
1. Defina cron para ser executado a cada minuto.
1. Abra três guias/janelas do terminal.
1. Vá para o diretório `root/base/project` do Adobe Commerce em cada janela do terminal.
1. Execute o seguinte comando em cada guia/janela:

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. Vá para o MySQL e execute a seguinte query:

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. Consulte grupos de tarefas agendadas para execução simultânea.

<u>Resultado esperado</u>: um cron `job_code` deve ser agendado para o período de tempo determinado.

<u>Resultado real</u>: há vários trabalhos cron agendados para o mesmo período.

## Solução

Para o Adobe Commerce nos estabelecimentos comerciais de infraestrutura em nuvem, [atualizar as ferramentas ECE](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) resolverá o problema.

Os comerciantes locais do Adobe Commerce devem aplicar um dos patches anexados para resolver o problema.

## Correções

Os patches estão anexados a este artigo. Para baixar o, role para baixo até o final do artigo e clique no nome do arquivo ou clique em um dos links a seguir:

* [Baixar MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)
* [Baixar MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)
* [Baixar MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* [Baixar MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)
* [Baixar MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)
* [Baixar MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)
* [Baixar MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)

### Versões compatíveis do Adobe Commerce

Os patches foram criados para determinada versão anotada no nome do arquivo de patch. Por exemplo, MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch foi criado para o Adobe Commerce 2.2.4 e é o melhor patch a ser usado para essa versão.

Os patches também são compatíveis com as seguintes versões:

* Para o Adobe Commerce no local 2.1.0-2.1.4: [Baixar MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip) O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:
   * Adobe Commerce na infraestrutura em nuvem 2.1.0 - 2.1.4
* Para o Adobe Commerce no local 2.1.5-2.1.12: [Baixar MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip) O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:
   * Adobe Commerce na infraestrutura em nuvem 2.1.5 - 2.1.12
* Para o Adobe Commerce na infraestrutura de nuvem 2.1.13: [Baixar MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* Para o Adobe Commerce no local 2.1.14-2.1.17: [Baixar MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip) O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:
   * Adobe Commerce no local 2.1.18
   * Adobe Commerce na infraestrutura em nuvem 2.1.14-2.1.18
* Para o Adobe Commerce no local 2.2.0-2.2.1: [Baixar MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip) O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:
   * Adobe Commerce na infraestrutura em nuvem 2.2.0 - 2.2.1
* Para o Adobe Commerce no local 2.2.0-2.2.3: [Baixar MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip) O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:
   * Adobe Commerce na infraestrutura em nuvem 2.2.0 - 2.2.3
* Para o Adobe Commerce no local 2.2.4: [Baixar MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip) O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:
   * Adobe Commerce na infraestrutura em nuvem 2.2.4

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de suporte, para obter instruções.

## Arquivos Anexados

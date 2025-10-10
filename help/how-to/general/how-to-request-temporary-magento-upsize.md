---
title: Como solicitar o Adobe Commerce temporário no upsize da infraestrutura em nuvem
description: Se sua organização estiver planejando um evento online em que você espera alto tráfego ou se você subitamente descobrir que seu site está passando por um evento de alto tráfego, poderá registrar um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar capacidade de nuvem adicional temporária para seu Adobe Commerce na loja de infraestrutura em nuvem.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: e59335b67e1f33e138e34cab93ce593836d14b48
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Como solicitar o Adobe Commerce temporário no upsize da infraestrutura em nuvem

Se sua organização estiver planejando um evento online em que você espera alto tráfego ou se você subitamente descobrir que seu site está passando por um evento de alto tráfego, poderá registrar um [Tíquete de Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar capacidade de nuvem adicional temporária para o Adobe Commerce na loja de infraestrutura em nuvem.

>[!NOTE]
>
>48 horas úteis de aviso são necessárias para solicitações de upsize sem emergência. Atualizações para campanhas promocionais não são consideradas emergências a menos que o site esteja completamente inoperante ou recebendo tráfego muito maior do que o previsto e o desempenho tenha sido severamente degradado.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Como identificar eventos de alto tráfego

No New Relic Alerts, você pode usar as condições de alerta da linha de base para definir limites que se ajustam ao comportamento de seus dados.

O alerta de linha de base é útil para criar condições de alerta que:

* Notifique você somente quando os dados estiverem se comportando de forma anormal.
* Ajustar-se dinamicamente à alteração de dados e tendências, incluindo tendências diárias ou semanais.

Além disso, os alertas de linha de base funcionam bem com novos aplicativos quando você ainda não tem comportamentos conhecidos.

New Relic Siga este link para saber mais sobre a [Detecção de anomalias com Inteligência aplicada](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

Se você receber uma notificação de alerta que sugira um evento de alto tráfego, talvez seja necessário considerar [enviar um Tíquete de Suporte](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) solicitando capacidade adicional. Siga as etapas abaixo.

## Como monitorar o desempenho do site

O Adobe fornece um conjunto de políticas de alerta do New Relic para a arquitetura de plano do Adobe Commerce na infraestrutura em nuvem Pro e a arquitetura de plano do Adobe Commerce na infraestrutura em nuvem Starter Ambientes de produção para rastrear as seguintes métricas principais de desempenho:

* [Pontuação do Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Taxa de erros
* Espaço em disco (disponível somente em ambientes de produção com arquitetura Pro)

Com base nas práticas recomendadas do setor, essas políticas definem limites para condições críticas e de advertência que afetam o desempenho. Quando seu site enfrenta um problema de infraestrutura ou aplicativo que aciona um limite de alerta, o New Relic envia notificações de alerta para que você possa resolver o problema de forma proativa. Para usar essas políticas, você deve configurar canais de notificação para receber as mensagens de alerta.

Siga este link para saber como [configurar alertas baseados em desempenho](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Etapas para solicitar o upsize temporário

Para solicitar capacidade de nuvem temporária adicional, envie um [Tíquete de Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para o Centro de Suporte da Adobe Commerce com as seguintes informações:

>[!NOTE]
>
>A opção *Solicitação de sobretensão de feriado* é apenas uma opção entre os meses de outubro e dezembro.

1. Selecione o produto [!DNL Adobe Commerce] para o qual você precisa de suporte:
   * [!DNL Commerce Cloud]
   * [!DNL Commerce on Managed Service]

1. Preencha os seguintes campos:
   * **[!UICONTROL Case Title]**
   * **[!UICONTROL Case Description]** *(descreva claramente o problema e o contexto.)*

1. Selecione *Solicitação de alteração de infraestrutura* no menu suspenso **[!UICONTROL Issue Reason]**.

1. Escolha o **[!UICONTROL Environment]** no menu suspenso.

1. Selecione o **[!UICONTROL Product Version]** apropriado no menu suspenso.

1. Escolha *Redimensionamento de Projeto em Nuvem (vCPU)* no menu suspenso **[!UICONTROL Which Infra Change you would like to do today]**.

1. **Selecione o[!UICONTROL Architecture]**:
   * *Arquitetura Padrão:* Selecione *Próximo Tamanho Disponível* no menu suspenso **Selecionar Tamanho**.
   * *Arquitetura em Escala:* Quando selecionada, a tela muda para mostrar dois campos adicionais:
      * *Tamanho do Nó da Web*
      * *Tamanho do Nó de Serviço* *(insira os tamanhos desejados para cada nó.)*

1. Insira o **[!UICONTROL From Date]** no formato UTC (data e hora).

1. Insira o **[!UICONTROL To Date]** no formato UTC (data e hora).

1. Fornecer **[!UICONTROL Project URL]** *(encontrado em https://accounts.magento.cloud/, normalmente no formato `https://[REGION].magento.cloud/projects/PROJECT_ID`)*

1. Insira o **[!UICONTROL Project ID]**.

1. Fornecer **[!UICONTROL Affected URL]** *(deve começar com `http://` ou `https://`.)*

1. Selecione **[!UICONTROL Priority]**.

1. Selecione **[!UICONTROL Business Impact]**.

1. Confirmar **[!UICONTROL Time Zone]** *(por exemplo, `(UTC-5:00) Indiana (East)`)*

1. Inserir **[!UICONTROL Phone Number]** *(por exemplo, `+12015550123`)*

1. Clique em **[!UICONTROL Submit]** para finalizar seu caso de suporte.

>[!NOTE]
>
>Depois que o upsize for agendado, um sistema automatizado ajustará o tamanho da instância da nuvem. Você pode não receber nenhuma notificação de tíquete quando o procedimento estiver concluído. Você pode usar a ferramenta Observation for Adobe Commerce para exibir seus tipos de instância do AWS ou do Azure para [verificar a alteração](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## Visualizar o histórico dos uploads

Você pode exibir o histórico de redimensionamentos solicitados solicitando as informações do seu **CSM (Customer Success Manager)**.
As seguintes informações estão disponíveis para cada solicitação de redimensionamento:

* **Data de Início do Tamanho**: data da solicitação de upsize.
* **Data de Término do Tamanho**: data em que o cluster retornou ao tamanho anterior.
* **Tamanho do vCPU**: o tamanho do cluster após o upsize.
* **Dias de Uso**: por quantos dias o cluster ficou com upsizing.
* **Period vCPU**: tamanho de vCPU alterado pelo número de dias em que foi usado. (por exemplo, o tamanho do vCPU 192 por 25 dias é igual a 4.800).


## Leitura relacionada

* Para obter insights, métodos e exemplos de como medir e melhorar o desempenho do site, consulte os seguintes artigos detalhados em nossa base de conhecimento de suporte:
   * [Cálculo de alocação de CPU para Adobe Commerce na nuvem](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Verifique se o upsize das instâncias do host é necessário para o Adobe Commerce na nuvem](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Verificar a configuração do CPU do host para o Adobe Commerce na nuvem](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Para obter informações sobre como identificar interrupções, consulte [Identificar e medir interrupções para o Adobe Commerce na nuvem](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) em nossa base de dados de conhecimento de suporte.
* Para obter informações sobre como melhorar o desempenho do site para evitar a necessidade de utilizar um aumento na capacidade, consulte estes artigos na documentação do desenvolvedor:
   * [Dimensionamento da imagem](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Armazenamento em cache de página inteira](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-Tools](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)

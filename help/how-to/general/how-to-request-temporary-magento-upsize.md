---
title: Como solicitar o Adobe Commerce temporário no upsize da infraestrutura em nuvem
description: Se sua organização estiver planejando um evento online em que você espera alto tráfego ou se você subitamente descobrir que seu site está passando por um evento de alto tráfego, poderá registrar um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar capacidade de nuvem adicional temporária para seu Adobe Commerce na loja de infraestrutura em nuvem.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Como solicitar o Adobe Commerce temporário no upsize da infraestrutura em nuvem

Se sua organização estiver planejando um evento online em que você espera alto tráfego ou se você subitamente descobrir que seu site está passando por um evento de alto tráfego, poderá registrar um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar capacidade de nuvem adicional temporária para o Adobe Commerce no cloud infrastructure store.

>[!NOTE]
>
>48 horas úteis de aviso são necessárias para solicitações de upsize sem emergência. Atualizações para campanhas promocionais não são consideradas emergências a menos que o site esteja completamente inoperante ou recebendo tráfego muito maior do que o previsto e o desempenho tenha sido severamente degradado.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, tudo [versões compatíveis](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Como identificar eventos de alto tráfego

No New Relic Alerts, você pode usar as condições de alerta da linha de base para definir limites que se ajustam ao comportamento de seus dados.

O alerta de linha de base é útil para criar condições de alerta que:

* Notifique você somente quando os dados estiverem se comportando de forma anormal.
* Ajustar-se dinamicamente à alteração de dados e tendências, incluindo tendências diárias ou semanais.

Além disso, os alertas de linha de base funcionam bem com novos aplicativos quando você ainda não tem comportamentos conhecidos.

Siga este link para saber mais sobre o New Relic [Detecção de anomalias com inteligência aplicada](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

Se você receber uma notificação de alerta que sugira um evento de tráfego alto, talvez seja necessário considerar [envio de um tíquete de suporte](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) solicitando capacidade adicional. Siga as etapas abaixo.

## Como monitorar o desempenho do site

O Adobe fornece um conjunto de políticas de alerta do New Relic para a arquitetura de plano Pro da infraestrutura do Adobe Commerce na nuvem e ambientes de produção da arquitetura de plano Starter do Adobe Commerce na infraestrutura da nuvem para rastrear as seguintes métricas principais de desempenho:

* [Pontuação do Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Taxa de erros
* Espaço em disco (disponível somente em ambientes de produção com arquitetura Pro)

Com base nas práticas recomendadas do setor, essas políticas definem limites para condições críticas e de advertência que afetam o desempenho. Quando seu site enfrenta um problema de infraestrutura ou aplicativo que aciona um limite de alerta, o New Relic envia notificações de alerta para que você possa resolver o problema de forma proativa. Para usar essas políticas, você deve configurar canais de notificação para receber as mensagens de alerta.

Siga este link para saber como [configurar alertas baseados em desempenho](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Etapas para solicitar o upsize temporário

Siga as etapas abaixo para enviar um [Tíquete de suporte](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) para solicitar capacidade de nuvem adicional temporária:

Enviar um [Tíquete de suporte no Centro de suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), após inserir as seguintes informações:

>[!NOTE]
>
>A variável *Solicitação de aumento de feriado* a opção é apenas uma opção entre outubro e dezembro de meses.

1. Selecione o produto da Adobe Commerce para o qual deseja obter suporte.
1. Preencha os primeiros quatro campos (Produto, Organização, Tipo de implementação, Assunto).
1. Selecionar *Infraestrutura em nuvem do Adobe Commerce* no **Motivo do contato** menu suspenso.
1. Selecionar *Solicitação de capacidade de aumento de feriado* no **Motivo do contato do Adobe Commerce Infrastructure** opções suspensas. Clique em **OK** na mensagem pop-up que solicita um aviso de 48 horas úteis para solicitações temporárias adicionais de capacidade na nuvem.
1. Selecionar datas para os campos obrigatórios **Redimensionar data de início** e **Redimensionar data final**. O preferido **Redimensionar hora de início** também é um campo obrigatório.
1. Preencha os próximos quatro campos.
1. No **Descrição** campo, se você tiver informações adicionais sobre o tamanho, insira-as aqui. Se nenhum tamanho maior específico for solicitado, faremos o upsizing até a próxima capacidade maior do tamanho do ambiente. As solicitações de sobretensão assumirão como padrão o próximo tamanho maior a partir do tamanho atual. Se você precisar de capacidade adicional, indique isso no campo **Descrição** campo. O aumento da capacidade será deduzido dos Dias de sobretensão contratados ou dos dias de vCPU. A janela típica de aumento de capacidade é de cinco dias, mas se você precisar de mais ou menos dias, indique isso em [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Depois que o upsize for agendado, um sistema automatizado ajustará o tamanho da instância da nuvem. Você pode não receber nenhuma notificação de tíquete quando o procedimento estiver concluído. Você pode usar a ferramenta Observation for Adobe Commerce para exibir os tipos de instância do AWS ou do Azure para [verificar a alteração](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## Visualizar o histórico dos uploads

Você pode visualizar o histórico dos redimensionamentos solicitados solicitando as informações de seu **CSM (Customer Success Manager, Gerente de sucesso do cliente)**.
As seguintes informações estão disponíveis para cada solicitação de redimensionamento:

* **Data de início do tamanho**: data da solicitação de upsize.
* **Data de término do tamanho**: data em que o cluster retornou ao tamanho anterior.
* **Tamanho do vCPU**: o tamanho do cluster após o upsize.
* **Dias de uso**: por quantos dias o cluster permaneceu com upsizing.
* **Período vCPU**: tamanho do vCPU alterado de acordo com o número de dias em que foi usado. (por exemplo, o tamanho do vCPU 192 por 25 dias é igual a 4.800).


## Leitura relacionada

* Para obter insights, métodos e exemplos de como medir e melhorar o desempenho do site, consulte os seguintes artigos detalhados em nossa base de conhecimento de suporte:
   * [Cálculo de alocação de CPU para o Adobe Commerce na nuvem](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Verifique se o upsize das instâncias do host é necessário para o Adobe Commerce na nuvem](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Verifique a configuração da CPU do host para o Adobe Commerce na nuvem](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Para obter informações sobre como identificar interrupções, consulte [Identificar e medir paralisações do Adobe Commerce na nuvem](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) em nossa base de conhecimento de suporte.
* Para obter informações sobre como melhorar o desempenho do site para evitar a necessidade de utilizar um aumento na capacidade, consulte estes artigos na documentação do desenvolvedor:
   * [Dimensionamento da imagem](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Armazenamento em cache de página inteira](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-Tools](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)

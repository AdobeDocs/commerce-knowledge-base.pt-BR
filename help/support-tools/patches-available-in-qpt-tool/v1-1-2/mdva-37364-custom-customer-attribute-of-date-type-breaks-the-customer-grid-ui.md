---
title: 'MDVA-37364: Atributo de cliente personalizado do tipo de data quebra a interface de grade'
description: O patch MDVA-37364 resolve o problema em que o atributo de cliente personalizado do tipo de data quebra a interface do usuário da Grade do cliente. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-37364. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.4.
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364: Atributo de cliente personalizado do tipo de data quebra a interface de grade

O patch MDVA-37364 resolve o problema em que o atributo de cliente personalizado do tipo de data quebra a interface do usuário da Grade do cliente. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-37364. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0-2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O atributo de cliente personalizado do tipo de data interrompe a interface do usuário da grade do cliente.

<u>Etapas a serem reproduzidas</u>:

1. Crie um atributo personalizado com tipo de data:
   * Vá para **Lojas** > **Atributos** > **Adicionar Atributo**.
   * Defina o Tipo de entrada como Data.
   * Defina as Opções Adicionar à Coluna como Sim.
   * Salve o atributo.
1. Vá para **Administrador** > **Clientes** > **Todos os Clientes**.
   * Adicione o atributo personalizado recém-adicionado à grade na opção de colunas.
1. Crie/edite um cliente e defina o valor do campo de atributo de data personalizado criado.
1. Salve, reindexe e limpe o cache.
1. Ir para **Clientes** > **Todos os Clientes**.
   * Verifique a Grade de Clientes.

<u>Resultados esperados</u>:

A Grade de clientes de administração mostra todos os dados, incluindo o novo atributo personalizado de data, sem romper a interface da Grade do cliente.

<u>Resultados reais</u>:

A interface do usuário da Grade de clientes de administração está com problemas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

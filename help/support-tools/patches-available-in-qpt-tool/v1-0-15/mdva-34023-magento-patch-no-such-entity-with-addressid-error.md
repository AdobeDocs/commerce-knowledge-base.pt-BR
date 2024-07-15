---
title: '''Patch MDVA-34023: erro "Entidade sem addressId"'
description: O patch MDVA-34023 resolve o problema em que os erros "Nenhuma entidade com addressId" ocorrem aleatoriamente no navegador da Web de um cliente.
exl-id: bdf8f97d-856a-4dd7-bf21-941d1493496c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Correção do MDVA-34023: erro &quot;Nenhuma entidade com addressId&quot;

O patch MDVA-34023 resolve o problema em que `No such entity with addressId` erros ocorrem aleatoriamente no navegador da Web de um cliente.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.1

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Lojas** > **Configurações** > **Configuração** > **Guia Clientes** > **Carrinho de compras persistente**.
1. Definir **Habilitar Persistência** = *Sim*, definir **Limpar Persistência na Saída** = *Não*.    ![persistent_shopping_cart_magento_2.4.1.png](/help/support-tools/patches-available-in-qpt-tool/assets/persistent_shopping_cart_magento_2.4.1.png)
1. Crie um novo cliente e defina os endereços padrão de entrega e cobrança.
1. Faça logout.
1. Faça logon com a caixa de seleção **Lembre-se de mim** marcada.
1. Vá para a tabela do banco de dados `customer_entity` e altere as IDs de `default_billing` e `default_shipping` para inexistentes.
1. Faça logout.

<u>Resultados esperados</u>:

Nenhum erro é exibido, conforme esperado.

<u>Resultados reais</u>:

O log de exceções é gerado:

```php
Exception.log:
{"0":"No such entity with addressId = XXXXX","1":"#0 /vendor\/magento\/module-customer\/Model\/AddressRegistry.php(49): Magento\\Framework
Exception
NoSuchEntityException::singleField('addressId', 'XXXXX')
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis em QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

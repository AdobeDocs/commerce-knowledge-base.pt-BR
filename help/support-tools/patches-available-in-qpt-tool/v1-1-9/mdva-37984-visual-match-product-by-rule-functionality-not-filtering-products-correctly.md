---
title: 'MDVA-37984: Merchandiser visual não está funcionando corretamente quando atualizações de preparo são aplicadas'
description: O patch MDVA-37984 resolve o problema em que a funcionalidade "Corresponder produto por regra" do Visual Merchandiser não filtra produtos corretamente quando atualizações de preparo são aplicadas. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-37984. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984: Merchandiser visual não está funcionando corretamente quando atualizações de preparo são aplicadas

O patch MDVA-37984 resolve o problema em que a funcionalidade &quot;Corresponder produto por regra&quot; do Visual Merchandiser não filtra produtos corretamente quando atualizações de preparo são aplicadas. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-37984. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A funcionalidade &quot;Corresponder produto por regra&quot; do Visual Merchandiser não filtra produtos corretamente quando atualizações de preparo são aplicadas.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma atualização de agendamento para qualquer produto existente.
   * Defina valores diferentes para `entity_id` e `row_id`.
1. Crie um novo produto configurável e, em seguida, um produto simples (para que os novos produtos `entity_id` e `row_ids` também sejam diferentes).
   * Para facilitar a replicação do problema, defina um valor de quantidade diferenciável para o produto simples - por exemplo, 5000.
1. Ir para uma categoria > **Produtos na categoria** e habilitar **Corresponder produtos por regra**.
1. Agora selecione &quot;Quantidade&quot; como o atributo, &quot;Maior&quot; como o operador e &quot;4500&quot; como o valor.
1. Clique em **salvar**.

<u>Resultados esperados</u>:

O produto configurável recém-criado é listado.

<u>Resultados reais</u>:

O produto configurável recém-criado não está listado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.

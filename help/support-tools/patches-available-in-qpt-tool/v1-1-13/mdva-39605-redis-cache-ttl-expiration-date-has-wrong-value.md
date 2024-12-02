---
title: 'MDVA-39605: valor incorreto de TTL de cache Redis (data de expiração)'
description: O patch MDVA-39605 resolve o problema em que o TTL (data de expiração) do cache Redis tem um valor incorreto. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-39605. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605: valor incorreto de TTL de cache Redis (data de expiração)

O patch MDVA-39605 resolve o problema em que o TTL (data de expiração) do cache Redis tem um valor incorreto. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-39605. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O TTL (data de expiração) do cache Redis tem um valor incorreto.

<u>Etapas a serem reproduzidas</u>:

Para testar a correção, limpe o cache e abra um produto configurável na loja. Em seguida, abra um terminal (console) e siga as etapas abaixo:

1. Execute o comando: `redis-cli`.
1. Execute `KEYS "*PRICE"` (deve haver apenas uma chave no resultado, por exemplo, `zc:ti:e54_PRICE`). Copie a chave.
1. Execute `SMEMBERS` seguido pela chave da etapa anterior (por exemplo, `SMEMBERS zc:ti:e54_PRICE`). Copie qualquer chave do resultado (por exemplo, e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Execute `KEYS "*<key>"` com o nome de chave da etapa anterior para obter o nome de chave completo (por exemplo, `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Deve haver apenas uma chave no resultado (por exemplo, `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Como você pode notar, o nome completo da chave é simplesmente o nome da chave com o prefixo &quot;`zc:k:`&quot;. Agora copie o nome completo da chave.
1. Execute `HGETALL` seguido do nome completo da chave da Etapa 4 para verificar o valor. O valor deve conter dados serializados de produtos associados de um produto configurável relacionado.
1. Execute `TTL` seguido do nome completo da chave na Etapa 4 para verificar se a chave tem uma expiração. O resultado deve ser diferente de **-1** e **-2** e deve ser aproximadamente 2592000 (30 dias). Embora a expiração definida no código seja de um ano, a biblioteca Redis usada no Adobe Commerce tem um limite rígido de expiração máxima de 2592000s.

<u>Resultados esperados</u>:

O limite de expiração é 2592000s

<u>Resultados reais</u>:

O limite de expiração está definido como **-1** ou **-2**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.

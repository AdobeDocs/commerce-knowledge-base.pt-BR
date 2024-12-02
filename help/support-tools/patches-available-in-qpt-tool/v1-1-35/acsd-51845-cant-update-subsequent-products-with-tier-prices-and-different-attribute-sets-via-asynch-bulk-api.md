---
title: 'ACSD-51845: não é possível atualizar produtos subsequentes com preços de camada e conjuntos de atributos diferentes por meio de um volume assíncrono [!DNL API]'
description: Aplique o patch ACSD-51845 para corrigir o problema do Adobe Commerce, em que não é possível atualizar produtos subsequentes com preços de camada e diferentes conjuntos de atributos por meio de massa assíncrona [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845: não é possível atualizar produtos subsequentes com preços de camada e conjuntos de atributos diferentes por meio de um volume assíncrono [!DNL API]

O patch ACSD-51845 corrige o problema em que você não pode atualizar produtos subsequentes com preços de camada e diferentes conjuntos de atributos por meio de [!DNL REST API] em massa assíncrono. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-51845. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Falha na atualização de produtos subsequentes com preços de camada e diferentes conjuntos de atributos por meio de [!DNL REST API] em massa assíncrono.

<u>Etapas a serem reproduzidas</u>:

1. Configurar [!DNL RabbitMQ].
1. Crie dois conjuntos de atributos.
1. Crie dois **Produtos Simples**, atribuindo cada produto a um conjunto de atributos diferente.
1. Adicione um **Preço de Grupo de Clientes** para cada produto.
1. Atualize ambos os produtos na mesma atualização em massa de [!DNL API].
1. Verifique se o comando `bin/magento queue:consumers:start async.operations.all` está em execução.
1. Verifique o status em massa de [!DNL API].

<u>Resultados esperados</u>:

A execução do serviço foi bem-sucedida.

<u>Resultados reais</u>:

O sistema retorna a mensagem de erro: *Não foi possível salvar o produto. Tente novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].

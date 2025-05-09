---
title: 'MDVA-42046: Valor incorreto atribuído ao atributo de produto'
description: O patch MDVA-42046 corrige o problema em que um valor incorreto é atribuído ao atributo de produto ao atualizar um produto que tem um campo de entrada de data. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-42046. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046: Valor incorreto atribuído ao atributo de produto

O patch MDVA-42046 corrige o problema em que um valor incorreto é atribuído ao atributo de produto ao atualizar um produto que tem um campo de entrada de data. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-42046. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.3.5-p2 e 2.4.0 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Depois de salvar um produto com campos `news_from_date` e/ou `news_to_date`, os valores desses campos são redefinidos para o padrão.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Exportar o produto criado na etapa um.
1. No arquivo CSV exportado, coloque alguns valores nos campos `news_from_date` e `news_to_date`. Por exemplo, 2021-05-15 e 2021-06-18.
1. Importe o produto usando o arquivo CSV modificado.
1. Adicione mais colunas &quot;Definir produto como novo a partir da data&quot; e &quot;Definir produto como novo a partir da data&quot; à grade de produtos.
1. Abra a página de edição do produto e, sem alterações, clique em **Salvar**.
1. Retorne à grade de produtos e verifique os dados do produto.

<u>Resultados esperados</u>:

Tanto a opção &quot;Definir produto como novo a partir da data&quot; quanto a opção &quot;Definir produto como novo até a data&quot; são iguais às opções antes de salvar.

<u>Resultados reais</u>:

* Os valores nas colunas &quot;Definir produto como novo a partir da data&quot; e &quot;Definir produto como novo até a data&quot; são alterados.

* A coluna &quot;Definir produto como novo a partir da data&quot; mostra a data atual e a coluna &quot;Definir produto como novo a partir da data&quot; está vazia.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) na documentação do desenvolvedor.

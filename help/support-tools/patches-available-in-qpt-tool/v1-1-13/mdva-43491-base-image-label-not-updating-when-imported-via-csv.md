---
title: 'MDVA-43491: Rótulo de imagem base não atualizado quando importado via CSV'
description: O patch MDVA-43491 corrige o problema em que o "base_image_label" não é atualizado quando importado por meio de um arquivo CSV para um site de várias lojas. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-43491. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: d744423a-f582-4410-8d66-861229cce1b5
feature: Data Import/Export
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-43491: Rótulo de imagem base não atualizado quando importado via CSV

O patch MDVA-43491 corrige o problema em que o `base_image_label` não é atualizado quando importado por meio de um arquivo CSV para um site de várias lojas. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-43491. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O `base_image_label` não é atualizado quando importado usando um arquivo CSV para um site de várias lojas.

<u>Pré-requisitos</u>:

Um ou mais sites, lojas e visualizações de loja não padrão existentes.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo produto.

   * Carregar uma imagem.
   * Atribua o produto aos sites recém-criados.

1. Exporte o produto como CSV.
1. Atualize o `base_image_label` para cada exibição de armazenamento duplicando a linha padrão do arquivo CSV.
1. Importe o arquivo CSV. Ele atualizará os rótulos de cada loja corretamente, o que pode ser verificado na guia **Imagens e Vídeos** da página de edição do produto.
1. Exporte o arquivo CSV novamente e atualize a coluna `base_image_label` com valores diferentes.
1. Importe o arquivo CSV novamente.
1. Abra o produto no Administrador e verifique se o rótulo foi atualizado para cada exibição de loja.

<u>Resultados esperados</u>:

O texto alternativo (rótulo da imagem) é atualizado com o valor específico do armazenamento de acordo com o arquivo CSV.

<u>Resultados reais</u>:

O texto alternativo (rótulo da imagem) não é atualizado com o valor `base_image_label` no arquivo CSV.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) na documentação do desenvolvedor.

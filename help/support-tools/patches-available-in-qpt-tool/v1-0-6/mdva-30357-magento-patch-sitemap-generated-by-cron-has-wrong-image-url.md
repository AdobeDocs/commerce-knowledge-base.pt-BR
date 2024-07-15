---
title: "MDVA-30357: o mapa de site gerado pelo cron tem URL de imagem incorreta"
description: O patch MDVA-30357 corrige o problema com o URL de imagem errado que está sendo criado por um mapa de site gerado pelo cron no administrador do Commerce. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
feature: Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-30357: o mapa de site gerado pelo cron tem URL de imagem incorreta

O patch MDVA-30357 corrige o problema com o URL de imagem errado que está sendo criado por um mapa de site gerado pelo cron no administrador do Commerce. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) 2.3.2 para 2.4.0

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os mapas de site gerados pelo cron no Adobe Commerce contêm o caminho de URL de imagem incorreto.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Commerce, crie uma nova visualização de site, loja ou loja.
1. Adicione pelo menos um produto a cada loja e adicione pelo menos uma imagem a cada produto.
1. Habilitar **Geração de Mapa do Site por Agendamento** em **Admin** > **Lojas** > **Configuração** > **CATÁLOGO** > **Mapa do Site XML** > **Configurações de Geração**.
1. Gere um mapa de site para qualquer um dos dois armazenamentos manualmente em **Admin** > **Marketing** > **Mapa do Site** usando um nome de mapa de site como &quot;*sitemap.xml*&quot;.
   * Renomeie o arquivo para algo como &quot;*manual\_sitemap.xml*&quot; ou copie o conteúdo do arquivo para qualquer editor de texto.
1. Gere o mesmo mapa de site pelo trabalho cron `sitemap_generate`.
1. Compare o mapa de site gerado manualmente &quot;*manual\_sitemap.xml*&quot; e o mapa de site gerado pelo cron &quot;*sitemap.xml*&quot;.

<u>Resultados esperados</u>:

A URL do caminho da imagem do mapa de site em cache está correta.

<u>Resultados reais</u>:

O mapa de site gerado pelo cron contém o URL de caminho de imagem incorreto. Se você tentar abrir a imagem a partir de &quot;*sitemap.xml*&quot;, ela mostrará um espaço reservado padrão. Os URLs de mapa de site gerados manualmente não são afetados por esse problema.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

Para saber mais sobre mapas de site, consulte estes artigos na documentação do desenvolvedor:

* [Adicionar robôs de mapa de site e mecanismo de pesquisa](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [Configurar e executar cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [Proteger cron.php para ser executado em um navegador](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)

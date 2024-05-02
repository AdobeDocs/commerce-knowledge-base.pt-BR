---
title: "Patch MDVA-33106: alterações de produto reagendadas apagadas após a execução do cron"
description: O patch MDVA-33106 corrige o problema em que as alterações de produto reagendadas são apagadas após o cron
exl-id: be32982c-796c-4069-ad70-37b5124ffb56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Patch MDVA-33106: alterações de produto reagendadas apagadas após a execução do cron

O patch MDVA-33106 corrige o problema em que as alterações de produto reagendadas são apagadas após o cron

```bash
bin/magento cron:run
```

é executado. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.13 está instalado. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. No Commerce Admin, acesse **Catálogo** > **Produtos** e clique em editar. Observe a **Preço** valor, por exemplo *9,99*.
1. Clique em **Agendar nova atualização** e preencha os detalhes:
   * O nome da atualização não é importante.
   * Defina uma data no futuro, +1 ano para a data inicial e a data final.
   * Definir preço para *1,99*.
   * Salve as alterações.
1. Vá para o painel Content staging e selecione a exibição de grade para ver se a correspondência agendada foi feita acima.
1. Selecione a ação de edição ao lado da atualização programada. Os dados ainda devem corresponder ao acima.
1. Mude a data agendada para algo mais próximo. Em vez de daqui a +1 ano, altere para + 1 semana ou + 1 mês.
1. Salve as alterações e verifique se as datas estão atualizadas no painel de preparo.
1. Aguarde a execução de um trabalho cron.
1. Clique em editar novamente na alteração agendada e verifique o preço.

<u>Resultados esperados</u>:

O preço é de 1,99.

<u>Resultados reais</u>:

O preço é 9,99.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

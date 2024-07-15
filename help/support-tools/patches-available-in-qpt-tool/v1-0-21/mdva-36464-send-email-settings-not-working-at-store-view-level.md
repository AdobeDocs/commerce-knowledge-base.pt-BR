---
title: "MDVA-36464: as configurações de envio de email não funcionam no nível da visualização de loja"
description: O patch MDVA-36464 corrige o problema em que as configurações de envio de email não funcionam no nível da visualização da loja. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalada. A ID do patch é MDVA-36464. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: cdf7e208-90ee-4711-8407-026da42fe3c8
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-36464: As configurações de envio de email não funcionam no nível de visualização da loja

O patch MDVA-36464 corrige o problema em que as configurações de envio de email não funcionam no nível da visualização da loja. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalada. A ID do patch é MDVA-36464. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.0-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisito:</u>

Instale o Adobe Commerce limpo.

<u>Etapas a serem reproduzidas</u>:

1. Crie um site, loja e exibição de loja adicionais (Neste exemplo, o segundo site é *site2*).
1. Desabilite a **Notificação por email** no nível global em **Armazenamento** > **Configuração** > **Avançado** > **Sistema** > **Configurações de Envio de Emails**.
1. Habilitar **Notificação por email** no nível do *site2* (**Desabilitar Comunicações por Email** = *Não*).
1. No Administrador, crie um novo usuário e atribua-o ao *site2*.
1. Em Admin, na página de edição do cliente, clique em **Redefinir senha** para o cliente criado acima na Etapa 4.

<u>Resultados esperados</u>:

O **email de boas-vindas** e o **email de redefinição de senha** são enviados, conforme esperado, porque **Desabilitar Comunicações por Email** = *Não* para o segundo site (Exemplo: *site2*).

<u>Resultados reais</u>:

* O **email de boas-vindas** após a criação do novo cliente não é acionado.
* O **email de redefinição de senha** não foi acionado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

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

O patch MDVA-36464 corrige o problema em que as configurações de envio de email não funcionam no nível da visualização da loja. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.21 está instalado. A ID do patch é MDVA-36464. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.0-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisito:</u>

Instale o Adobe Commerce limpo.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma visualização adicional de site, loja e loja (neste exemplo, o segundo site é *site2*).
1. Desativar **Notificação por e-mail** a nível mundial no **Loja** > **Configuração** > **Avançado** > **Sistema** > **Configurações de envio de email**.
1. Ativar **Notificação por e-mail** no *site2* nível (**Desabilitar Comunicações por Email** = *Não*).
1. Em Administração, crie um novo usuário e atribua-o à *site2*.
1. Em Administração, na página de edição do cliente, clique em **Redefinir senha** para o cliente criado acima na Etapa 4.

<u>Resultados esperados</u>:

Ambos os **email de boas-vindas** e a variável **redefinir email de senha** são enviadas, conforme esperado, porque **Desabilitar Comunicações por Email** = *Não* para o segundo site (Exemplo: *site2*).

<u>Resultados reais</u>:

* A variável **email de boas-vindas** após a criação do novo cliente não for acionada.
* A variável **redefinir email de senha** não é acionado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

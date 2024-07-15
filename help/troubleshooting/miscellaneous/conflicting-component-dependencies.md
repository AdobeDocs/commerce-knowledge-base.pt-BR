---
title: Dependências de componentes em conflito
description: Este artigo fornece uma solução para dependências de componentes conflitantes. Ao tentar configurar ou atualizar o Adobe Commerce usando o Assistente de configuração da Web, você verá a mensagem de erro do compositor *"Encontramos dependências de componentes conflitantes"*.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 8f0f7412e75e07a22e66236b88c095c698dbf23e
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Dependências de componentes em conflito

Este artigo fornece uma solução para dependências de componentes conflitantes. Ao tentar configurar ou atualizar o Adobe Commerce usando o Assistente para Configuração da Web, você verá a mensagem de erro *&quot;Encontramos dependências de componentes conflitantes&quot;* do Composer.

## Produtos e versões afetados

* Adobe Commerce no local 2.2.x, 2.3.x
* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Problema {#issue}

Uma mensagem de erro de dependências de componente conflitantes semelhante ao seguinte (os nomes e as versões reais dos pacotes variam):

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## Causa

Essa mensagem será exibida se o Composer não puder determinar quais componentes instalar ou atualizar.

## Solução

Dois cenários principais podem levar a dependências de componentes conflitantes. Clique em seu cenário para obter etapas de solução de problemas.

* [Atualização do Adobe Commerce](#upgrading-magento)
* [Incompatibilidade com módulos de terceiros:](#incompatibility-third-party-modules)
   * [Adobe Commerce (todos os tipos de implantação)](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## Atualização do Adobe Commerce {#upgrading-magento}

Se você estiver atualizando o Adobe Commerce na infraestrutura em nuvem, tente o seguinte para resolver dependências de componentes conflitantes:

* Verifique as chaves que estão sendo usadas para a atualização. As chaves estão sendo geradas na conta de email correta?
* Verifique as permissões e certifique-se de que elas correspondam aos requisitos de atualização de Magento. Revise [Visão geral de atualização do Magento > Lista de verificação de atualização e atualização > Permissões do sistema de arquivos](https://devdocs.magento.com/guides/v2.3/comp-mgr/prereq/prereq_compman-checklist.html#perms) na documentação do desenvolvedor.

## Incompatibilidade com módulos de terceiros: {#incompatibility-third-party-modules}

Dependências de componentes em conflito também podem ser causadas por módulos de terceiros que dependem de componentes do Commerce anteriores aos que você instalou. Tente o seguinte:

1. No [exemplo](#issue) anterior, o pacote instalado magento/sample-data versão 0.74.0-beta15 não pode ser atualizado para 1.0.0-beta. No entanto, 0.74.0-beta15 pode ser atualizado para 0.74.0-beta16 (ou outros). Edite `composer.json` para fazer qualquer uma dessas alterações. Normalmente, as versões que seu projeto está solicitando serão definidas na propriedade `require` ou `require-dev` do objeto nesse arquivo JSON. Dependendo das opções de versões de pacote fornecidas, elas podem especificar uma versão específica ou uma restrição. Para orientação geral sobre como usar o Composer, se você estiver em nossa infraestrutura em nuvem, consulte [Nuvem para Adobe Commerce > Tecnologias e requisitos > Composer](https://devdocs.magento.com/cloud/reference/cloud-composer.html#files) em nossa documentação do desenvolvedor. Se você estiver no Adobe Commerce no local, consulte [Adobe Commerce > Guia de Instalação > Instalar o Adobe Commerce usando o Composer](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html).
1. Agora, tente a verificação de preparação. Revise [Visão geral de atualização do Adobe Commerce > Executar o Gerenciador de módulos > Etapa 1 Verificação de disponibilidade](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-readiness.html) em nossa documentação do desenvolvedor.
1. Se a verificação de preparação falhar com outra mensagem de falha de verificação de dependência do Componente, clique nos links a seguir, dependendo se você está usando o [Adobe Commerce](#magento-commerce-magento-commerce-cloud) ou o [Magento Open Source](#opensource) para obter mais etapas de solução de problemas.

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. Entre em contato com o desenvolvedor da extensão para que ele possa ajudá-lo. Você pode encontrar as informações de contato na página da qual você comprou a extensão no Commerce Marketplace. Procure o botão **Contatar Vendedor** exibido no painel direito. Todos os desenvolvedores do Commerce devem fornecer um guia do usuário e de instalação quando publicarem uma extensão no Marketplace. Você pode encontrar ambos no lado direito da landing page.
1. Se você não receber uma resposta do Vendedor em um período de tempo razoável, [entre em contato com o Suporte do Marketplace](mailto:commercemarketplacesupport@adobe.com) para que possamos lembrá-los de seus compromissos de suporte ao cliente.

## Magento Open Source {#opensource}

Solicite assistência no [nosso fórum principal](https://community.magento.com/) ou [contate um Parceiro do Adobe Commerce](https://magento.com/find-a-partner) que ajude nas questões do Open Source.

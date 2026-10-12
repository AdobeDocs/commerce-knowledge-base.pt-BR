---
title: Posso instalar aplicativos de terceiros na minha instância da nuvem?
description: Não. Não é permitido instalar aplicativos de terceiros (como WordPress ou Drupal) no Adobe Commerce em servidores de infraestrutura em nuvem. Você deve hospedar esses aplicativos em servidores externos.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%
---
# Posso instalar aplicativos de terceiros na minha instância da nuvem?

Não. Não é permitido instalar aplicativos de terceiros (como WordPress ou Drupal) no Adobe Commerce em servidores de infraestrutura em nuvem. Você deve hospedar esses aplicativos em servidores externos.

## Motivos

### Termos do contrato de serviço

O Adobe Commerce na edição [Contrato de Termos de Serviço](https://magento.com/legal/terms/cloud-terms) da infraestrutura em nuvem estabelece o seguinte em seu artigo 18:

> O Cliente concorda que a Adobe Commerce e o Serviço não serão usados para hospedar outros aplicativos de software de terceiros que não sejam diretamente dependentes do Software.

Por ser uma solução em nuvem, a Adobe assume total responsabilidade pela segurança do servidor. Para garantir alta segurança, só permitimos a hospedagem do aplicativo do Adobe Commerce no servidor de nuvem dedicado.

### Conformidade com o PCI

Como um Provedor de soluções de nível 1 com certificação PCI, a Adobe Commerce na infraestrutura em nuvem deve seguir o Padrão de Segurança de Dados PCI e certificar-se de:

>.. Desenvolver e manter sistemas e aplicativos seguros
> ([Abordagem da Adobe para conformidade com o PCI](https://magento.com/pci-compliance) Requisito 6, Manter um programa de gerenciamento de vulnerabilidades)

Como a Adobe não pode garantir a conformidade com o PCI de aplicativos de terceiros, a instalação desses aplicativos em servidores na nuvem não é permitida.

## Dica: use as extensões do Commerce Marketplace para obter melhores integrações

Para melhorar a integração do seu aplicativo Adobe Commerce na infraestrutura em nuvem com as soluções de terceiros hospedadas em servidores externos, recomendamos que você use as extensões do [Commerce Marketplace](https://marketplace.magento.com) que podem ser adequadas à sua finalidade.

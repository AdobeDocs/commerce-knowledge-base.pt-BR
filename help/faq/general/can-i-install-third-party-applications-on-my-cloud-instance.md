---
title: Posso instalar aplicativos de terceiros na minha instância da nuvem?
description: Não. Não é permitido instalar aplicativos de terceiros (como WordPress ou Drupal) no Adobe Commerce em servidores de infraestrutura em nuvem. Você deve hospedar esses aplicativos em servidores externos.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Posso instalar aplicativos de terceiros na minha instância da nuvem?

Não. Não é permitido instalar aplicativos de terceiros (como WordPress ou Drupal) no Adobe Commerce em servidores de infraestrutura em nuvem. Você deve hospedar esses aplicativos em servidores externos.

## Motivos

### Termos do contrato de serviço

O Adobe Commerce na edição [Contrato de Termos de Serviço](https://magento.com/legal/terms/cloud-terms) da infraestrutura em nuvem estabelece o seguinte em seu artigo 18:

> O Cliente concorda que a Adobe Commerce e o Serviço não serão usados para hospedar outros aplicativos de software de terceiros que não sejam diretamente dependentes do Software.

Por ser uma solução em nuvem, o Adobe assume total responsabilidade pela segurança do servidor. Para garantir alta segurança, só permitimos a hospedagem do aplicativo do Adobe Commerce no servidor de nuvem dedicado.

### Conformidade com o PCI

Como um Provedor de soluções de nível 1 com certificação PCI, a Adobe Commerce na infraestrutura em nuvem deve seguir o Padrão de Segurança de Dados PCI e certificar-se de:

>.. Desenvolver e manter sistemas e aplicativos seguros
> ([Abordagem de Adobe para conformidade com o PCI](https://magento.com/pci-compliance), Requisito 6, Manter um programa de gerenciamento de vulnerabilidades)

Como o Adobe não pode garantir a conformidade com o PCI de aplicativos de terceiros, a instalação desses aplicativos em servidores na nuvem não é permitida.

## Dica: use as extensões do Commerce Marketplace para obter melhores integrações

Para melhorar a integração do seu aplicativo Adobe Commerce na infraestrutura em nuvem com as soluções de terceiros hospedadas em servidores externos, recomendamos que você use as extensões [Commerce Marketplace](https://marketplace.magento.com) que podem ser adequadas à sua finalidade.

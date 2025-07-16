---
title: O número máximo de cookies seria excedido devido a um erro no Adobe Commerce
description: Saiba como resolver o problema do Adobe Commerce em que ocorre um erro informando que o número máximo de cookies seria excedido.
feature: Deploy, Support, Upgrade, Tools and External Services
role: Admin, Developer
exl-id: 5c42ea7a-f023-4d34-8417-bb470efc3b84
source-git-commit: 87e98607ee5e1cc41e4266836fd09531a290725e
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# *O número máximo de cookies seria excedido* erro no Adobe Commerce

Este artigo fornece patches para resolver o erro informando *O número máximo de cookies seria excedido* no Adobe Commerce.

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7, com um dos seguintes patches aplicados:

* Patch MDVA-12304 aplicado usando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/release-notes)
* [Atualização de segurança disponível para o Adobe Commerce - APSB25-08](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-27149)
* [Patches da nuvem para [!DNL Commerce] 1.1.4](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)

## Problema

Problemas relacionados aos cookies no Adobe Commerce estão fazendo com que o seguinte erro apareça nos logs de erro:

*report.WARNING: não é possível enviar o cookie. O número máximo de cookies seria excedido.*

### Causa

O problema ocorre porque o número máximo de cookies permitidos está definido como *50*.

## Solução

1. Remova o patch MDVA-12304 se você o aplicar usando o [!DNL Quality Patches Tool (QPT)].

   * Para o Adobe Commerce na infraestrutura em nuvem, remova o patch de `.magento.env.yaml`.
   * Para instalações locais do Adobe Commerce, execute o seguinte comando para reverter o patch:

     `vendor/bin/magento/quality-patches revert MDVA-12304`

1. Aplique os patches anexados de acordo com sua versão do Adobe Commerce:

   * Para as versões 2.4.4-p12, 2.4.5-p11, 2.4.6-p9 e 2.4.7-p4, aplique o [patch ACSD-64710](assets/acsd-64710_2.4.5-p11.patch.zip).

   * Para as versões 2.4.4-p13, 2.4.5-p12, 2.4.6-p10, 2.4.7-p5 e 2.4.8, aplique o [patch ACSD-65562](assets/acsd-65562_2.4.5-p12.patch.zip).

### Leitura relacionada

* [Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/upgrade-guide/patches/apply) no guia de atualização do Adobe Commerce
* [Práticas recomendadas para distribuir patches do Adobe Commerce em escala](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale) no Manual de implementação do Adobe Commerce
* [Notas de versão do Conjunto de ferramentas do Commerce Cloud](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) no Guia do Commerce na Nuvem.

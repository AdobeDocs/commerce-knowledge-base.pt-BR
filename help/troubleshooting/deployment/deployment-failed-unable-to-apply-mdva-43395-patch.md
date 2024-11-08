---
title: "Falha na implantação: não é possível aplicar o patch MDVA-43395"
description: Este artigo fornece uma solução para o problema, em que tentar aplicar o patch MDVA-43395 resulta em falha na implantação.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Falha na implantação: não é possível aplicar o patch MDVA-43395

Este artigo fornece uma solução para o problema, em que tentar aplicar o patch MDVA-43395 resulta em falha na implantação.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

Você não pode aplicar o patch MDVA-43395.

## Causa

Os comerciantes da nuvem não precisam aplicar o patch MDVA-43395 separadamente se tiverem o [magento/magento-cloud-patches 1.0.16](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016) instalado, que já inclui o patch.

## Solução

Para resolver o problema, remova os patches MDVA-43395 e MDVA-43443 do diretório `m2-hotfixes` e reimplante.

Se você puder aplicar o patch MDVA-43443 por meio do diretório `m2-hotfixes`, ainda precisará removê-lo, como mencionado acima. As versões futuras do Adobe Commerce já terão esses patches contidos neles, portanto, a implantação poderá falhar se você fizer a atualização mais tarde.

Para verificar se o patch foi aplicado, execute o comando `vendor/bin/magento-patches -n status |grep 43443`.
Se ele mostrar vários resultados como este, você deverá remover o patch MDVA-43443 da pasta `m2-hotfixes`:

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Leitura relacionada

* [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.
* [Patches da nuvem para o Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016) em nossa documentação para desenvolvedores.

---
title: Substituir Gráficos de Imagem do Google depreciados por Gráficos de Imagem
description: Atualmente, a maioria das edições e versões do Adobe Commerce usa [Gráficos de imagem do Google](https://developers.google.com/chart/image/) para renderizar gráficos estáticos em painéis de Administração. A partir de 14 de março de 2019, a Google deixará de oferecer suporte aos Gráficos de imagem do Google. Para resolver esse problema, estamos fornecendo um patch para substituir os Gráficos de imagem do Google pelo serviço gratuito [Image-Charts](https://www.image-charts.com/).
exl-id: f86f0bb9-8a03-471d-8696-1eba4b8acbd1
feature: Cache, Compliance
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Substituir Gráficos de Imagem do Google depreciados por Gráficos de Imagem

A maioria das edições e versões do Adobe Commerce atualmente usam [Gráficos de imagem do Google](https://developers.google.com/chart/image/) para renderizar gráficos estáticos nos painéis de Administração. A partir de 14 de março de 2019, a Google deixará de oferecer suporte aos Gráficos de imagem do Google. Para resolver esse problema, estamos fornecendo uma correção para substituir os Gráficos de imagem do Google por [Gráficos de imagens](https://www.image-charts.com/) serviço gratuito.

## Versões afetadas

* Adobe Commerce 1.X, todas as edições
* Adobe Commerce 2.X, todas as edições

>[!NOTE]
>
>O Adobe Commerce no local 1.14.4.1, Magento Open Source 1.9.4.1, o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.3.2 incluirão esta atualização de gráfico. A atualização para essas versões continua o suporte para gráficos de imagem sem patches adicionais.

## Problema

A Google interrompeu o suporte aos Gráficos de imagem do Google em 14 de março de 2019. Os usuários das versões Adobe Commerce 1.X e Adobe Commerce 2.2.X não poderão exibir gráficos estáticos, a menos que façam download e apliquem o patch, substituindo os Gráficos de imagem da Google pela solução Gráficos de imagem. Os gráficos exibidos terão o mesmo design e funcionalidade dos Gráficos de imagem do Google por meio do serviço de conta gratuita Gráficos de imagem com uma [GDPR](https://www.image-charts.com/data-processing-addendum.html) conformidade com a política de privacidade. Para obter opções adicionais, consulte [Gráficos de imagens](https://www.image-charts.com/).

## Solução

Para poder exibir gráficos estáticos no Commerce Admin, baixe e aplique o patch fornecido pelo Adobe Commerce. Nenhuma configuração adicional é necessária.

### Adobe Commerce no local

1. Salve o [anexado MAGETWO-98833\_composer\_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.zip) e faça upload para o diretório raiz do Adobe Commerce.
1. Execute o seguinte comando SSH, tendo substituído o nome do patch pelo nome real:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch
   ```

   Se o comando acima não funcionar, tente usar `-p2` em vez de `-p1`.)

1. Para que as alterações sejam refletidas, atualize o cache no Administrador em **Sistema** > **Gerenciamento de cache**.

### Adobe Commerce na infraestrutura em nuvem

Para os comerciantes da Cloud, o patch será incluído na atualização de ferramentas ECE mais próxima.

### Magento 2 Open Source

1. Ir para [https://magento.com/tech-resources/download\#download2291](https://magento.com/tech-resources/download#download2291).
1. No **Selecionar seu formato** selecione a versão do compositor e clique em **Baixar**.
1. Faça upload do patch no diretório raiz do Adobe Commerce.
1. Execute o seguinte comando SSH, tendo substituído o nome do patch pelo nome real:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-37-48.patch
   ```

   (Se o comando acima não funcionar, tente usar `-p2` em vez de `-p1`.)

1. Para que as alterações sejam refletidas, atualize o cache no Administrador em **Sistema** > **Gerenciamento de cache**.

### Adobe Commerce 1 no local

Siga estas etapas para baixar e aplicar o patch:

1. Salve o [anexado MPERF-10509-EE-2019-03-13-06-32-19.diff](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff.zip) e faça upload para o diretório raiz do Adobe Commerce.
1. Execute o seguinte comando SSH:

   ```git
   patch -p1 < MPERF-10509-EE-2019-03-13-06-32-19.diff
   ```

   (Se o comando acima não funcionar, tente usar `-p2` em vez de `-p1`.)

1. Para que as alterações sejam refletidas, atualize o cache no Administrador em **Sistema** > **Gerenciamento de cache**.

### Magento 1 Código aberto

Siga estas etapas para baixar e aplicar o patch:

1. Clique em [**este link**](https://magento.com/tech-resources/download#download2283) para localizar o Patch de Gráficos do Painel de Administração.
1. Selecionar

   ```git
   MPERF-10509.diff
   ```

   do **Selecionar seu formato** e clique em Download.

1. Faça upload do arquivo para o diretório raiz do Adobe Commerce.
1. Execute o seguinte comando SSH:

   ```git
   patch -p1 < MPERF-10509.diff
   ```

   (Se o comando acima não funcionar, tente usar `-p2` em vez de `-p1`.)

1. Para que as alterações sejam refletidas, atualize o cache no Administrador em **Sistema** > **Gerenciamento de cache**.

## Arquivos Anexados

[Baixar MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch)

[Baixar MPERF-10509-EE-2019-03-13-06-32-19.diffh](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff)

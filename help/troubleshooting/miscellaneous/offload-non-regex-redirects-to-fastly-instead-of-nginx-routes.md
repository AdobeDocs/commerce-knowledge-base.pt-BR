---
title: 'Descarregar redirecionamentos não-[!DNL regex] para [!DNL Fastly] em vez de [!DNL Nginx] (rotas)'
description: Este tópico sugere uma solução para um problema típico de desempenho de redirecionamentos que você pode ter ao descarregar redirecionamentos não-[!DNL regex] para [!DNL Fastly] em vez de [!DNL Nginx] no Adobe Commerce na infraestrutura em nuvem.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Descarregar redirecionamentos não-[!DNL regex] para [!DNL Fastly] em vez de [!DNL Nginx] (rotas)

Este tópico sugere uma solução para um problema típico de desempenho de redirecionamentos que você pode ter ao descarregar redirecionamentos não-[!DNL regex] para [!DNL Fastly] em vez de [!DNL Nginx] no Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem (todas as versões) em ambientes `Master/Production/Staging` aproveitando o [!DNL Fastly]

## Problema

Na infraestrutura em nuvem do Adobe Commerce, um grande número de redirecionamentos/regravações que não são [!DNL regex] não pode ser feito na camada [!DNL Nginx] e, como resultado, pode causar problemas de desempenho.

## Causa

O arquivo `routes.yaml` no diretório `.magento/routes.yaml` define as rotas do Adobe Commerce na infraestrutura de nuvem.

Se o tamanho do arquivo do `routes.yaml` for de 32 KB ou maior, você deverá descarregar os redirecionamentos/regravações não-[!DNL regex] no [!DNL Fastly].

Essa camada [!DNL Nginx] não pode lidar com um grande número de redirecionamentos/regravações que não sejam [!DNL regex], ou ocorrerão problemas de desempenho.

## Solução

A solução é descarregar esses redirecionamentos não-[!DNL regex] para [!DNL Fastly]. Crie um caminho de erro genérico para redirecionar para [!DNL Fastly].

As etapas a seguir detalharão como colocar redirecionamentos em [!DNL Fastly] em vez de [!DNL Nginx].

1. Crie um dicionário do Edge.

   Primeiro, você pode usar [[!DNL VCL] trechos no Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) para definir um dicionário de borda. Ele conterá os redirecionamentos.

   Algumas limitações:

   * [!DNL Fastly] não pode fazer [!DNL regex] nas entradas do dicionário. É só uma combinação exata. Para obter mais informações sobre essas limitações, consulte os documentos de [[!DNL Fastly] sobre as limitações do dicionário de borda](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * [!DNL Fastly] tem um limite de 1000 entradas em um único dicionário. [!DNL Fastly] pode expandir esse limite, mas isso leva à terceira advertência.
   * Sempre que você atualizar as entradas e implantar o [!DNL VCL] atualizado em todos os nós, há um aumento de tempo de carregamento geométrico com dicionários em expansão. Isso significa que um dicionário de 2000 entradas carregará de fato de 3x a 4x mais lento do que um dicionário de 1000 entradas. Mas isso só é um problema quando você está implantando o [!DNL VCL] (atualizando o dicionário ou alterando o código da função [!DNL VCL]).

     Isso não afeta o tempo que [!DNL Fastly] leva para processar uma solicitação; afeta apenas o tempo que [!DNL Fastly] leva para enviar uma nova configuração.

     De modo geral, as alterações de configuração levam em média alguns segundos, geralmente não mais do que 5 a 10 segundos. Portanto, um aumento de 2x nos itens do dicionário leva mais de 30 segundos para que sua configuração seja implementada. Um aumento de 4x levaria mais perto de 2 minutos. Isso leva à quarta advertência.

   * Há um limite bem rígido de 10.000 entradas em um dicionário de borda.

   É altamente recomendável consolidar sua lista de redirecionamentos. Você pode usar vários dicionários, mas esteja ciente de que qualquer atualização feita no [!DNL VCL] levará vários minutos para realmente popular através do [!DNL Fastly].

1. Comparar o [!DNL URL] ao(s) Dicionário(s).

   Quando a pesquisa [!DNL URL] ocorrer, a comparação será feita para aplicar o código de erro personalizado se uma correspondência for encontrada.

   Use outro trecho [!DNL VCL] para adicionar algo como o seguinte a `vcl_recv`:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Aqui, estamos verificando se o [!DNL URL] existe na entrada da tabela. Em caso positivo, estamos chamando um erro interno [!DNL Fastly] e transmitindo para esse erro o redirecionamento [!DNL URL] da tabela.

1. Gerenciar o redirecionamento.

   Quando uma correspondência é encontrada, a ação executada é definida para aquele `obj.status`, neste caso, um redirecionamento de movimentação permanente 301.

   Use um trecho final em `vcl_error` para enviar os códigos de erro 301 de volta ao cliente:

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Com este bloco, estamos verificando se o código de erro transmitido de `vcl_recv` corresponde e, em caso positivo, definiremos o local para a mensagem de erro transmitida, alteraremos o código de status para 301 e a mensagem para &quot;Movido Permanentemente&quot;. Nesse momento, a resposta deve estar pronta para retornar ao cliente.

### Serviço de preparo

>[!WARNING]
>
>Se você quiser experimentar todas essas etapas, é altamente recomendável configurar um ambiente de preparo do Adobe Commerce. Dessa forma, você pode executar testes no serviço [!DNL Fastly] para verificar se tudo se comporta como você esperaria.

Se você não quiser executar um ambiente de preparo do Adobe Commerce, mas quiser ver a aparência desses redirecionamentos, poderá configurar uma conta de preparo diretamente no [!DNL Fastly].

## Leitura relacionada

* [[!DNL Fastly VCL] referência](https://docs.fastly.com/vcl/)
* [Configurar rotas](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) na documentação do desenvolvedor
* [Configure [!DNL Fastly]](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) em nossa documentação do desenvolvedor
* [[!DNL VCL] folha de características de expressão regular](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) em nossa documentação do desenvolvedor
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

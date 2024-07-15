---
title: Descarga de redirecionamentos não regex para Fastly em vez de Nginx (rotas)
description: Este tópico sugere uma solução para um problema típico de desempenho de redirecionamentos que você pode ter ao descarregar redirecionamentos não regex para o Fastly em vez de Nginx no Adobe Commerce na infraestrutura em nuvem.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Descarga de redirecionamentos não regex para Fastly em vez de Nginx (rotas)

Este tópico sugere uma solução para um problema típico de desempenho de redirecionamentos que você pode ter ao descarregar redirecionamentos não regex para o Fastly em vez de Nginx no Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem (todas as versões) ambientes `Master/Production/Staging` aproveitando o Fastly

## Problema

No Adobe Commerce na infraestrutura em nuvem, um grande número de redirecionamentos/regravações não regex não pode ser feito na camada do Nginx e, como resultado, pode causar problemas de desempenho.

## Causa

O arquivo `routes.yaml` no diretório `.magento/routes.yaml` define as rotas do Adobe Commerce na infraestrutura de nuvem.

Se o tamanho do arquivo do `routes.yaml` for de 32 KB ou maior, você deverá descarregar os redirecionamentos/regravações não regex no Fastly.

Essa camada do Nginx não pode lidar com um grande número de redirecionamentos/regravações não regex, caso contrário ocorrerão problemas de desempenho.

## Solução

Em vez disso, a solução é descarregar esses redirecionamentos não regex para o Fastly. Crie um caminho de erro genérico para redirecionar para o Fastly.

As etapas a seguir detalharão como colocar redirecionamentos no Fastly em vez de no Nginx.

1. Crie um dicionário do Edge.

   Primeiro, você pode usar [trechos de VCL no Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) para definir um dicionário de borda. Ele conterá os redirecionamentos.

   Algumas limitações:

   * O Fastly não pode fazer regex nas entradas do dicionário. É só uma combinação exata. Para obter mais informações sobre essas limitações, consulte os [documentos do Fastly sobre as limitações do dicionário de borda](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * O Fastly tem um limite de 1000 entradas em um único dicionário. O Fastly pode expandir esse limite, mas isso leva à terceira advertência.
   * Sempre que você atualizar as entradas e implantar essa VCL atualizada em todos os nós, há um aumento de tempo de carga geométrica com dicionários em expansão. Isso significa que um dicionário de 2000 entradas carregará de fato de 3x a 4x mais lento do que um dicionário de 1000 entradas. Mas isso só é um problema quando você está implantando o VCL (atualizando o dicionário ou alterando o código da função do VCL).

     Isso não afeta o tempo que o Fastly leva para processar uma solicitação, mas afeta apenas o tempo que o Fastly leva para enviar uma nova configuração.

     De modo geral, as alterações de configuração levam em média alguns segundos, geralmente não mais do que 5 a 10 segundos. Portanto, um aumento de 2x nos itens do dicionário leva mais de 30 segundos para que sua configuração seja implementada. Um aumento de 4x levaria mais perto de 2 minutos. Isso leva à quarta advertência.

   * Há um limite bem rígido de 10.000 entradas em um dicionário de borda.

   É altamente recomendável consolidar sua lista de redirecionamentos. Você pode usar vários dicionários, mas esteja ciente de que qualquer atualização feita no VCL levará vários minutos para ser realmente preenchida pelo Fastly.

1. Compare o URL com o(s) dicionário(s).

   Quando a pesquisa de URL ocorrer, a comparação será feita para aplicar o código de erro personalizado se uma correspondência for encontrada.

   Use outro trecho VCL para adicionar algo como o seguinte a `vcl_recv`:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Aqui, estamos verificando se o URL existe na entrada da tabela. Em caso positivo, estamos chamando um erro interno do Fastly e transmitindo para esse erro o URL de redirecionamento da tabela.

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
>Se você quiser experimentar todas essas etapas, é altamente recomendável configurar um ambiente de preparo do Adobe Commerce. Dessa forma, você pode executar testes no serviço Fastly para verificar se tudo se comporta como você esperaria.

Se você não quiser executar um ambiente de preparo do Adobe Commerce, mas quiser ver como esses redirecionamentos serão, é possível configurar uma conta de preparo diretamente no Fastly.

## Leitura relacionada

* [Referência de VCL do Fastly](https://docs.fastly.com/vcl/)
* [Configure as rotas](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) na documentação do desenvolvedor.
* [Configure o Fastly](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) em nossa documentação do desenvolvedor.
* [Folha de características de expressão regular de VCL](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) em nossa documentação do desenvolvedor.

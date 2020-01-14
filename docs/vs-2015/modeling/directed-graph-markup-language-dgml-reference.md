---
title: Referência de DGML (grafo Markup Language) Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: cc3e4ae7-60fa-4e22-9227-98020b480b73
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c676c57d6e6e6008611133235df8d525752f16b5
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849497"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Referência DGML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A DGML (grafo Markup Language) descreve informações usadas para visualização e para executar a análise de complexidade, e é o formato usado para persistir mapas de código no Visual Studio. Ele usa XML simples para descrever grafos direcionados acíclico e cíclicos. Um gráfico direcionado é um conjunto de nós conectados por links ou bordas. Nós e links podem ser usados representam estruturas de rede como, por exemplo, elementos em um projeto de software.

 Observe que algumas versões do Visual Studio dão suporte apenas a um subconjunto de recursos DGML, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Quando você edita um arquivo .dgml, o IntelliSense ajuda você a identificar atributos disponíveis para cada elemento e seus valores. Para especificar a cor em um atributo, use nomes de cores comuns como, por exemplo, "Azul", ou valores hexadecimais ARGB, como "#ffa0b1c3". DGML usa um subconjunto pequeno de formatos de definição de cor do WPF (Windows Presentation Foundation). Para obter mais informações, consulte a [classe Colors](https://msdn.microsoft.com/library/system.windows.media.colors.aspx).

## <a name="DGML"></a>Sintaxe de DGML
 A tabela a seguir descreve os tipos de elementos que são usados em DGML:

- `<DirectedGraph></DirectedGraph>`

   Esse é o elemento raiz do documento de mapa de código (. dgml). Todos os outros elementos de DGML são exibidos no escopo desse elemento.

   A seguinte lista descreve atributos opcionais que é possível incluir:

   `Background`-a cor do plano de fundo do mapa

   `BackgroundImage`-o local de um arquivo de imagem a ser usado como plano de fundo do mapa.

   `GraphDirection`-quando o mapa é definido como layout de árvore (`Sugiyama`), organize os nós para que a maioria dos links flua na direção especificada: `TopToBottom`, `BottomToTop`, `LeftToRight`ou `RightToLeft`. Consulte [alterar o layout do mapa](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout`-defina o mapa para os seguintes layouts: `None`, `Sugiyama` (layout de árvore), `ForceDirected` (clusters rápidos) ou `DependencyMatrix`. Consulte [alterar o layout do mapa](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance`-quando o mapa é definido como layout de árvore ou de clusters rápidos, mostre somente os nós que são um número especificado (1-7) de links distantes dos nós selecionados. Consulte [alterar o layout do mapa](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   Exemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   Esse elemento opcional contém uma lista de elementos `<Node/>`, que definem nós no mapa. Para obter mais informações, consulte o elemento `<Node/>`.

  > [!NOTE]
  > Quando você faz referência a um nó indefinido em um elemento `<Link/>`, o mapa cria um elemento de `<Node/>` automaticamente.

   Exemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   Esse elemento define um único nó. Ele é exibido na lista de elementos `<Nodes><Nodes/>`.

   Esse elemento deve incluir os seguintes atributos:

   `Id`-o nome exclusivo do nó e o valor padrão do atributo `Label`, se nenhum atributo `Label` separado for especificado. Esse nome deve corresponder ao atributo `Source` ou `Target` do link que faz referência a ele.

   A seguinte lista descreve alguns dos atributos opcionais que é possível incluir:

   `Label`-o nome de exibição do nó.

   Atributos de estilo. Consulte [Personalizar mapa de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category`-o nome de uma categoria que identifica elementos que compartilham este atributo. Para obter mais informações, consulte o elemento `<Category/>`.

   `Property`-o nome de uma propriedade que identifica elementos que têm o mesmo valor de propriedade. Para obter mais informações, consulte o elemento `<Property/>`.

   `Group`-se o nó contiver outros nós, defina esse atributo como `Expanded` ou `Collapsed` para mostrar ou ocultar seu conteúdo. Deve haver um elemento `<Link/>` que inclua o atributo `Category="Contains"` e especifique o nó pai como o nó de origem e o nó filho como o nó de destino. Consulte [elementos de código de grupo](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility`-defina esse atributo como `Visible`, `Hidden`ou `Collapsed`. Usa `System.Windows.Visibility`. Consulte [ocultar ou mostrar nós e links](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference`-defina esse atributo para vincular a um documento ou URL. Consulte [vincular documentos ou URLs a elementos de código e links](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

   Exemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   Esse elemento contém a lista de elementos `<Link>`, que definem links entre nós. Para obter mais informações, consulte o elemento `<Link/>`.

   Exemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   Esse elemento define um único link que conecta um nó de origem a um nó de destino. Ele é exibido na lista de elementos `<Links></Links>`.

  > [!NOTE]
  > Se esse elemento fizer referência a um nó indefinido, o documento de mapa criará automaticamente um nó que tem os atributos especificados, se houver.

   Esse elemento deve incluir os seguintes atributos:

   `Source`-o nó de origem do link

   `Target`-o nó de destino do link

   A seguinte lista descreve alguns dos atributos opcionais que é possível incluir:

   `Label`-o nome de exibição do link

   Atributos de estilo. Consulte [Personalizar mapa de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category`-o nome de uma categoria que identifica elementos que compartilham este atributo. Para obter mais informações, consulte o elemento `<Category/>`.

   `Property`-o nome de uma propriedade que identifica elementos que têm o mesmo valor de propriedade. Para obter mais informações, consulte o elemento `<Property/>`.

   Exemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   Esse elemento contém a lista de elementos `<Category/>`. Para obter mais informações, consulte o elemento `<Category/>`.

   Exemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   Esse elemento define um atributo `Category`, que é usado para identificar os elementos que compartilham esse atributo. Um atributo `Category` pode ser usado para organizar elementos do mapa, fornecer atributos compartilhados por meio de herança ou definir metadados adicionais.

   Esse elemento deve incluir os seguintes atributos:

   `Id`-o nome exclusivo da categoria e o valor padrão do atributo `Label`, se nenhum atributo `Label` separado for especificado.

   A seguinte lista descreve alguns dos atributos opcionais que é possível incluir:

   `Label`-um nome amigável para o leitor para a categoria.

   `BasedOn`-a categoria pai da qual o `<Category/>` do elemento atual é herdado.

   No exemplo desse elemento, a categoria `FailedTest` herda seu atributo `Stroke` da categoria `PassedTest`. Consulte "para criar categorias hierárquicas" em [Personalizar mapas de código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   As categorias também fornecem algum comportamento de modelo básico que controla a aparência de nós e links quando eles são exibidos em um mapa. Consulte [Personalizar mapa de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Exemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   Esse elemento contém a lista de elementos `<Property/>`. Para obter mais informações, consulte o elemento `<Property/>`.

   Exemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   Esse elemento define um atributo `Property` que é possível usar para atribuir um valor a qualquer elemento ou atributo DGML, inclusive categorias e outras propriedades.

   Esse elemento deve incluir os seguintes atributos:

  - `Id`-o nome exclusivo da propriedade e o valor padrão do atributo `Label`, se nenhum atributo `Label` separado for especificado.

  - `DataType`-o tipo de dados armazenados pela propriedade

    Se você quiser que a propriedade apareça na janela **Propriedades** , use a propriedade `Label` para especificar o nome de exibição da propriedade.

    Consulte [atribuir categorias a elementos de código e links](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

    Exemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

### <a name="AddAlias"></a>Aliases para caminhos usados com frequência
 A substituição dos caminhos mais usados por aliases ajuda a reduzir o tamanho do arquivo .dgml e o tempo necessário para carregar ou salvar o arquivo. Para criar um alias, adicione uma seção `<Paths></Paths>` ao final do arquivo .dgml. Nesta seção, adicione um elemento `<Path/>` para definir um alias para o caminho:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

 Para fazer referência ao alias de um elemento no arquivo. dgml, coloque o `Id` do elemento \<Path/> com um sinal de cifrão ($) e parênteses (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Veja também
 [As dependências de mapa em suas soluções](../modeling/map-dependencies-across-your-solutions.md) [usam mapas de código para depurar seus aplicativos para](../modeling/use-code-maps-to-debug-your-applications.md) [Localizar possíveis problemas usando analisadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md)

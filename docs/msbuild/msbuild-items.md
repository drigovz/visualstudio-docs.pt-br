---
title: Itens do MSBuild | Microsoft Docs
description: Saiba como usar o atributo de inclusão do MSBuild do rowgroup para especificar os arquivos a serem incluídos em uma compilação.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a28823a1a492cb1e8d5f434f98248fecc5d84e47
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904505"
---
# <a name="msbuild-items"></a>Itens do MSBuild

Itens do MSBuild são entradas no sistema de build e eles normalmente representam arquivos (os arquivos estão especificados no atributo `Include`). Os itens são agrupados em tipos de item com base em seus nomes de elemento. Os tipos de item são listas nomeadas de itens que podem ser usados como parâmetros para tarefas. As tarefas usam os valores do item para executar as etapas do processo de build.

 Como os itens são nomeados pelo tipo de item ao qual pertencem, os termos “item” e “valor de item” podem ser usados alternadamente.

## <a name="create-items-in-a-project-file"></a>Criar itens em um arquivo de projeto

 Os itens são declarados no arquivo de projeto como elementos filho de um elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md). O nome do elemento filho é o tipo do item. O atributo `Include` do elemento especifica os itens (arquivos) a serem incluídos com esse tipo de item. Por exemplo, o XML a seguir cria um tipo de item chamado `Compile`, que inclui dois arquivos.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 O item *file2.cs* não substitui o item *file1.cs* ; em vez disso, o nome do arquivo é anexado à lista de valores para o `Compile` tipo de item.

 O XML a seguir cria o mesmo tipo de item declarando os dois arquivos em um atributo `Include`. Observe que os nomes de arquivo são separados por ponto e vírgula.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

O `Include` atributo é um caminho que é interpretado em relação à pasta do arquivo de projeto, $ (MSBuildProjectPath), mesmo que o item esteja em um arquivo importado, como um arquivo *. targets* .

## <a name="create-items-during-execution"></a>Criar itens durante a execução

 Os itens que estão fora dos elementos de [destino](../msbuild/target-element-msbuild.md) são valores designados durante a fase de avaliação de um build. Durante a fase de execução subsequente, os itens podem ser criados ou modificados das seguintes maneiras:

- Qualquer tarefa pode emitir um item. Para emitir um item, o elemento [Task](../msbuild/task-element-msbuild.md) deve ter um elemento filho [Output](../msbuild/output-element-msbuild.md) que tem um atributo `ItemName`.

- A tarefa [CreateItem](../msbuild/createitem-task.md) pode emitir um item. Esse uso é preterido.

- A partir do .NET Framework 3.5, os elementos `Target` podem conter elementos [ItemGroup](../msbuild/itemgroup-element-msbuild.md) que podem conter elementos de item.

## <a name="reference-items-in-a-project-file"></a>Referenciar itens em um arquivo de projeto

 Para referenciar tipos de item em todo o arquivo de projeto, use a sintaxe @(\<ItemType>). Por exemplo, você faria referência no tipo de item no exemplo anterior usando `@(Compile)`. Usando esta sintaxe, você pode passar itens para tarefas, especificando o tipo de item como um parâmetro dessa tarefa. Para obter mais informações, consulte [como: selecionar os arquivos a serem compilados](../msbuild/how-to-select-the-files-to-build.md).

 Por padrão, os itens de um tipo de item são separados por ponto e vírgula (;) quando são expandidos. Você pode usar a sintaxe @ ( \<ItemType> , ' \<separator> ') para especificar um separador diferente do padrão. Para obter mais informações, consulte [como exibir uma lista de itens separados por vírgulas](../msbuild/how-to-display-an-item-list-separated-with-commas.md).

## <a name="use-wildcards-to-specify-items"></a>Usar curingas para especificar itens

Você pode usar os caracteres curinga `**`, `*` e `?` para especificar um grupo de arquivos como entradas para um build em vez de listar cada arquivo separadamente.

- O caractere curinga `?` corresponde a um único caractere.
- O caractere curinga `*` corresponde a zero ou mais caracteres.
- A sequência de caracteres curinga `**` corresponde a um caminho parcial.

Por exemplo, você pode especificar todos os arquivos `.cs` no diretório que contém o arquivo de projeto usando o elemento a seguir no arquivo de projeto.

```xml
<CSFile Include="*.cs"/>
```

O seguinte elemento seleciona todos os arquivos `.vb` na unidade `D:`:

```xml
<VBFile Include="D:/**/*.vb"/>
```

Para incluir caracteres literais `*` ou `?` em um item sem expansão de curinga, você deve [usar o escape para os caracteres curinga](../msbuild/how-to-escape-special-characters-in-msbuild.md).

Para obter mais informações sobre caracteres curinga, confira [Como selecionar os arquivos a serem compilados](../msbuild/how-to-select-the-files-to-build.md).

## <a name="use-the-exclude-attribute"></a>Usar o atributo Exclude

 Os elementos de item podem conter o atributo `Exclude`, que exclui itens específicos (arquivos) do tipo de item. O atributo `Exclude` normalmente é usado junto com caracteres curinga. Por exemplo, o XML a seguir adiciona cada arquivo *.cs* no diretório ao tipo de item CSFile, exceto o arquivo *DoNotBuild.cs* .

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 O atributo `Exclude` afeta somente os itens adicionados pelo atributo `Include` no elemento do item que contém ambos. O exemplo a seguir não excluiria o arquivo *Form1.cs* , que foi adicionado no elemento item anterior.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Para obter mais informações, consulte [como excluir arquivos da compilação](../msbuild/how-to-exclude-files-from-the-build.md).

## <a name="item-metadata"></a>Metadados do item

 Os itens que podem conter metadados, além das informações nos atributos `Include` e `Exclude`. Esses metadados podem ser usados por tarefas que exigem mais informações sobre os itens ou para os destinos e tarefas de lote. Para obter mais informações, consulte [Envio em lote](../msbuild/msbuild-batching.md).

 Os metadados são uma coleção de pares chave-valor que são declarados no arquivo de projeto como elementos filho de um elemento do item. O nome do elemento filho é o nome dos metadados e o valor do elemento filho é o valor dos metadados.

 Os metadados são associados ao elemento do item que os contém. Por exemplo, o XML a seguir adiciona metadados `Culture` que têm o valor `Fr` aos itens *one.cs* e *two.cs* do tipo de item CSFile.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Um item pode ter zero ou mais valores de metadados. Você pode alterar os valores de metadados a qualquer momento. Se definir metadados para um valor vazio, você efetivamente vai removê-lo do build.

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Referenciar metadados de item em um arquivo de projeto

 Você pode fazer referência a metadados de item em todo o arquivo de projeto usando a sintaxe %(\<ItemMetadataName>). Se existir a ambiguidade, você poderá qualificar uma referência usando o nome do tipo de item. Por exemplo, você pode especificar%( \<ItemType.ItemMetaDataName> ). O exemplo a seguir usa os metadados de exibição para o lote da tarefa de mensagem. Para obter mais informações sobre como usar os metadados de item para o envio em lote, confira [Metadados de item no envio de tarefas em lote](../msbuild/item-metadata-in-task-batching.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Stuff Include="One.cs" >
            <Display>false</Display>
        </Stuff>
        <Stuff Include="Two.cs">
            <Display>true</Display>
        </Stuff>
    </ItemGroup>
    <Target Name="Batching">
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>
    </Target>
</Project>
```

### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Metadados de item conhecido

 Sempre que um item é adicionado a um tipo de item, esse item é atribuído a alguns metadados conhecidos. Por exemplo, todos os itens têm o%(de metadados bem conhecido \<Filename> ), cujo valor é o nome do arquivo do item (sem a extensão). Para obter mais informações, confira [Metadados de item conhecidos](../msbuild/msbuild-well-known-item-metadata.md).

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Transformar os tipos de item usando metadados

 Você pode transformar listas de itens em novas listas de item usando metadados. Por exemplo, você pode transformar um tipo de item `CppFiles` que tem itens que representam arquivos *.cpp* em uma lista correspondente de arquivos *.obj* usando a expressão `@(CppFiles -> '%(Filename).obj')`.

 O código a seguir cria um tipo de item `CultureResource` que contém cópias de todos os itens `EmbeddedResource` com metadados `Culture`. O valor de metadados `Culture` se torna o valor dos novos metadados `CultureResource.TargetDirectory`.

```xml
<Target Name="ProcessCultureResources">
    <ItemGroup>
        <CultureResource Include="@(EmbeddedResource)"
            Condition="'%(EmbeddedResource.Culture)' != ''">
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>
        </CultureResource>
    </ItemGroup>
</Target>
```

 Para obter mais informações, consulte [Transformações](../msbuild/msbuild-transforms.md).

## <a name="item-definitions"></a>Definições de item

 A partir do .NET Framework 3.5, você pode adicionar metadados padrão a qualquer tipo de item usando o [elemento ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Como metadados conhecidos, os metadados padrão estão associados a todos os itens do tipo de item especificado. Você pode substituir explicitamente metadados padrão em uma definição de item. Por exemplo, o XML a seguir fornece aos itens `Compile`*one.cs* e *three.cs* os metadados `BuildDay` com o valor "Monday". O código fornece ao item *two.cs* os metadados `BuildDay` com o valor "Tuesday".

```xml
<ItemDefinitionGroup>
    <Compile>
        <BuildDay>Monday</BuildDay>
    </Compile>
</ItemDefinitionGroup>
<ItemGroup>
    <Compile Include="one.cs;three.cs" />
    <Compile Include="two.cs">
        <BuildDay>Tuesday</BuildDay>
    </Compile>
</ItemGroup>
```

 Para obter mais informações, confira [Definições de item](../msbuild/item-definitions.md).

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Atributos de itens em um ItemGroup de um Target

 A partir do .NET Framework 3.5, os elementos `Target` podem conter elementos [ItemGroup](../msbuild/itemgroup-element-msbuild.md) que podem conter elementos de item. Os atributos nesta seção são válidos quando são especificados para um item em um `ItemGroup` que é um `Target`.

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Remover atributo

 O atributo `Remove` remove itens específicos (arquivos) do tipo de item. Esse atributo foi introduzido no .NET Framework 3,5 (somente dentro de destinos). Os destinos dentro e fora têm suporte a partir do MSBuild 15,0.

 O exemplo a seguir remove todos os arquivos *.config* do tipo de item Compile.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> Atributo KeepMetadata

 Se um item for gerado em um destino, o elemento de item poderá conter o atributo `KeepMetadata`. Se esse atributo for especificado, apenas os metadados que serão especificados na lista de nomes separados por ponto-e-vírgula serão transferidos do item de origem para o item de destino. Um valor vazio para esse atributo é equivalente a não especificação dele. O atributo `KeepMetadata` foi introduzido no .NET Framework 4.5.

 O exemplo a seguir mostra como usar o atributo `KeepMetadata`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0">

    <ItemGroup>
        <FirstItem Include="rhinoceros">
            <Class>mammal</Class>
            <Size>large</Size>
        </FirstItem>

    </ItemGroup>
    <Target Name="MyTarget">
        <ItemGroup>
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />
        </ItemGroup>

        <Message Text="FirstItem: %(FirstItem.Identity)" />
        <Message Text="  Class: %(FirstItem.Class)" />
        <Message Text="  Size:  %(FirstItem.Size)"  />

        <Message Text="SecondItem: %(SecondItem.Identity)" />
        <Message Text="  Class: %(SecondItem.Class)" />
        <Message Text="  Size:  %(SecondItem.Size)"  />
    </Target>
</Project>

<!--
Output:
  FirstItem: rhinoceros
    Class: mammal
    Size:  large
  SecondItem: rhinoceros
    Class: mammal
    Size:
-->
```

### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> Atributo RemoveMetadata

 Se um item for gerado em um destino, o elemento de item poderá conter o atributo `RemoveMetadata`. Se esse atributo for especificado, todos os metadados serão transferidos do item de origem para o item de destino, exceto os metadados cujos nomes estão contidos na lista de nomes separados por ponto-e-vírgula. Um valor vazio para esse atributo é equivalente a não especificação dele. O atributo `RemoveMetadata` foi introduzido no .NET Framework 4.5.

 O exemplo a seguir mostra como usar o atributo `RemoveMetadata`.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <MetadataToRemove>Size;Material</MetadataToRemove>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)" />
        <Message Text="  Size:     %(Item1.Size)" />
        <Message Text="  Color:    %(Item1.Color)" />
        <Message Text="  Material: %(Item1.Material)" />
        <Message Text="Item2: %(Item2.Identity)" />
        <Message Text="  Size:     %(Item2.Size)" />
        <Message Text="  Color:    %(Item2.Color)" />
        <Message Text="  Material: %(Item2.Material)" />
    </Target>
</Project>

<!--
Output:
  Item1: stapler
    Size:     medium
    Color:    black
    Material: plastic
  Item2: stapler
    Size:
    Color:    black
    Material:
-->
```

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> Atributo KeepDuplicates

 Se um item for gerado em um destino, o elemento de item poderá conter o atributo `KeepDuplicates`. `KeepDuplicates` é um atributo `Boolean` que especifica se um item deverá ser adicionado ao grupo de destino se for uma duplicata exata de um item existente.

 Se os itens de origem e de destino tiverem o mesmo valor Include, mas metadados diferentes, o item será adicionado mesmo se `KeepDuplicates` estiver definido como `false`. Um valor vazio para esse atributo é equivalente a não especificação dele. O atributo `KeepDuplicates` foi introduzido no .NET Framework 4.5.

 O exemplo a seguir mostra como usar o atributo `KeepDuplicates`.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Item1 Include="hourglass;boomerang" />
        <Item2 Include="hourglass;boomerang" />
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item1 Include="hourglass" KeepDuplicates="false" />
            <Item2 Include="hourglass" />
        </ItemGroup>

        <Message Text="Item1: @(Item1)" />
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />
        <Message Text="Item2: @(Item2)" />
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />
    </Target>
</Project>

<!--
Output:
  Item1: hourglass;boomerang
    hourglass  Count: 1
    boomerang  Count: 1
  Item2: hourglass;boomerang;hourglass
    hourglass  Count: 2
    boomerang  Count: 1
-->
```

## <a name="updating-metadata-on-items-in-an-itemgroup-outside-of-a-target"></a>Atualizando metadados em itens em um item de grupo fora de um destino

Os itens fora dos destinos podem ter seus metadados existentes atualizados por meio do `Update` atributo. Este atributo **não** está disponível para itens sob destinos.

```xml
<Project>
    <PropertyGroup>
        <MetadataToUpdate>pencil</MetadataToUpdate>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Color>red</Color>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="notebook">
            <Size>SMALL</Size>
            <Color>YELLOW</Color>
        </Item2>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="$(MetadataToUpdate);stapler;er*r;@(Item2)" Price="10" Material="">
            <Color>RED</Color>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: RED
    Material:
    Price: 10
Item1: pencil
    Size: small
    Color: RED
    Material:
    Price: 10
Item1: eraser
    Size:
    Color: RED
    Material:
    Price: 10
Item1: notebook
    Size: large
    Color: RED
    Material:
    Price: 10
-->
```

:::moniker range=">=vs-2019"
No MSBuild versão 16,6 e posteriores, o `Update` atributo dá suporte a referências de metadados qualificados para facilitar a importação de metadados de dois ou mais itens.

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item3 Include="notebook">
            <Size>SMALL</Size>
            <Color>BLUE</Color>
            <Price>20</Price>
        </Item3>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="@(Item2);er*r;@(Item3)" Size="%(Size)" Color="%(Item2.Color)" Price="%(Item3.Price)" Model="2020">
            <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: black
    Material: plastic
    Price:
    Model:
Item1: pencil
    Size: small
    Color: RED
    Material: Premium PLASTIC
    Price:
    Model: 2020
Item1: eraser
    Size: small
    Color:
    Material: gum
    Price:
    Model: 2020
Item1: notebook
    Size: large
    Color:
    Material: paper
    Price: 20
    Model: 2020
-->
```

Comentários:
- Os metadados não qualificados (% (M)) são associados ao tipo de item que está sendo atualizado ( `Item1` no exemplo acima). Os metadados qualificados ( `%(Item2.Color)` ) são associados dentro do conjunto de tipos de item de correspondência capturados da expressão de atualização.
- Se um item corresponder várias vezes dentro e entre vários itens referenciados:
  - A última ocorrência de cada tipo de item referenciado é capturada (portanto, um item capturado por tipo de item).
  - Isso corresponde ao comportamento do envio em lote de item de tarefa em destinos.
- Onde um pode colocar referências de%():
  - Metadados
  - Condições de metadados
- A correspondência de nome de metadados não diferencia maiúsculas de minúsculas.
:::moniker-end

## <a name="updating-metadata-on-items-in-an-itemgroup-of-a-target"></a>Atualizando metadados em itens em um rowgroup de um destino

Os metadados também podem ser modificados dentro de destinos, por uma sintaxe menos expressiva do que `Update` :

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item2 Include="ruler">
            <Color>GREEN</Color>
        </Item2>

    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <!-- Metadata can be expressed either as attributes or as elements -->
            <Item1 Size="GIGANTIC" Color="%(Item2.Color)">
                <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
            </Item1>
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: pencil
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: eraser
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: notebook
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
-->
```

## <a name="see-also"></a>Veja também

- [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)
- [Itens de projeto comuns do MSBuild](../msbuild/common-msbuild-project-items.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Como selecionar os arquivos a serem compilados](../msbuild/how-to-select-the-files-to-build.md)
- [Como excluir arquivos da compilação](../msbuild/how-to-exclude-files-from-the-build.md)
- [Como exibir uma lista de itens separados por vírgulas](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Definições de item](../msbuild/item-definitions.md)
- [Envio em lote](../msbuild/msbuild-batching.md)

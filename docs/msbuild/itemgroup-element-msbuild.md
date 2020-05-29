---
title: Elemento ItemGroup (MSBuild) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c058a5986f72192a86d0e554d9e0d0b9bdce1b42
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173506"
---
# <a name="itemgroup-element-msbuild"></a>Elemento ItemGroup (MSBuild)

Contém um conjunto de elementos [Item](../msbuild/item-element-msbuild.md) definidos pelo usuário. Cada item usado em um projeto do MSBuild deve ser especificado como um filho de um `ItemGroup` elemento.

\<Project>
\<ItemGroup>

## <a name="syntax"></a>Sintaxe

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Condition`|Atributo opcional. Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|
|`Label`|Atributo opcional. Identifica o `ItemGroup`.|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Define as entradas do processo de build. Pode não haver nenhum ou pode haver mais de um elemento `Item` em um `ItemGroup`.|

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Elemento raiz necessário de um arquivo de projeto do MSBuild. |
| [Destino](../msbuild/target-element-msbuild.md) | A partir do .NET Framework 3.5, o elemento `ItemGroup` pode aparecer dentro de um elemento `Target`. Para obter mais informações, consulte [Destinos](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Exemplo

O exemplo de código a seguir mostra as coleções de itens definidos pelo usuário `Res` e `CodeFiles`, declaradas dentro de um elemento `ItemGroup`. Cada um dos itens na coleção de itens `Res` contém um elemento [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) filho definido pelo usuário.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

Em um arquivo de projeto simples, você normalmente usa um único `ItemGroup` elemento, mas também pode usar vários `ItemGroup` elementos. Quando vários `ItemGroup` elementos são usados, os itens são combinados em um único `ItemGroup` . Por exemplo, alguns itens podem ser incluídos por um `ItemGroup` elemento separado que é definido em um arquivo importado.

Os RowGroups podem ter condições aplicadas usando o `Condition` atributo. Nesse caso, os itens só serão adicionados à lista de itens se a condição for satisfeita. Consulte as [condições do MSBuild](msbuild-conditions.md)

## <a name="see-also"></a>Veja também

- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [Itens](../msbuild/msbuild-items.md)
- [Itens de projeto comuns do MSBuild](../msbuild/common-msbuild-project-items.md)

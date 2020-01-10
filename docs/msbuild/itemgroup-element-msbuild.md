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
ms.openlocfilehash: 588118bf31c5d310e947b02fda476a63d0d9df7a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573437"
---
# <a name="itemgroup-element-msbuild"></a>Elemento ItemGroup (MSBuild)
Contém um conjunto de elementos [Item](../msbuild/item-element-msbuild.md) definidos pelo usuário. Cada item usado em um projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deve ser especificado como filho de um elemento `ItemGroup`.

\<Project> \<ItemGroup>

## <a name="syntax"></a>Sintaxe

```xml
<ItemGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.

### <a name="attributes"></a>{1&gt;{2&gt;Atributos&lt;2}&lt;1}

|Atributo|Descrição|
|---------------|-----------------|
|`Condition`|Atributo opcional. Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Child elements

|Elemento|Descrição|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Define as entradas do processo de build. Pode não haver nenhum ou pode haver mais de um elemento `Item` em um `ItemGroup`.|

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Projeto](../msbuild/project-element-msbuild.md) | Elemento raiz necessário de um arquivo de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| [Target](../msbuild/target-element-msbuild.md) | A partir do .NET Framework 3.5, o elemento `ItemGroup` pode aparecer dentro de um elemento `Target`. Para obter mais informações, consulte [Destinos](../msbuild/msbuild-targets.md). |

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

## <a name="see-also"></a>Veja também
- [Referência de esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [Itens](../msbuild/msbuild-items.md)
- [Itens de projeto comuns do MSBuild](../msbuild/common-msbuild-project-items.md)

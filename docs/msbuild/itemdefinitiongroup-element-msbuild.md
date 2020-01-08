---
title: Elemento ItemDefinitionGroup (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5bfe09fec169495afa5b58a41f7c9f1b9bacfad
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573463"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>Elemento ItemDefinitionGroup (MSBuild)
O elemento `ItemDefinitionGroup` permite definir um conjunto de Definições de Item, que são valores de metadados aplicados por padrão a todos os itens do projeto. ItemDefinitionGroup substitui a necessidade de usar a [tarefa CreateItem](../msbuild/createitem-task.md) e [tarefa CreateProperty](../msbuild/createproperty-task.md). Para obter mais informações, confira [Definições de item](../msbuild/item-definitions.md).

\<Project> \<ItemDefinitionGroup>

## <a name="syntax"></a>Sintaxe

```xml
<ItemDefinitionGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemDefinitionGroup>
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
|[Item](../msbuild/item-element-msbuild.md)|Define as entradas do processo de build. Pode não haver nenhum ou pode haver mais de um elemento `Item` em um `ItemDefinitionGroup`.|

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Projeto](../msbuild/project-element-msbuild.md) | Elemento raiz necessário de um arquivo de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="example"></a>Exemplo
O exemplo de código a seguir define dois itens de metadados, m e n, em um ItemDefinitionGroup. Nesse exemplo, os metadados padrão "m" são aplicados ao Item "i" porque os metadados "m" não estão explicitamente definidos pelo Item "i". No entanto, os metadados padrão "n" não são aplicados ao Item "i" porque os metadados "n" já estão definidos pelo Item "i".

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemDefinitionGroup>
        <i>
            <m>m1</m>
            <n>n1</n>
        </i>
    </ItemDefinitionGroup>
    <ItemGroup>
        <i Include="a">
            <o>o1</o>
            <n>n2</n>
        </i>
    </ItemGroup>
    ...
</Project>
```

## <a name="see-also"></a>Veja também
- [Referência de esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [Itens](../msbuild/msbuild-items.md)

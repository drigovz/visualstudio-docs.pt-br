---
title: Elemento Output (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90fbd517608c9c36db0b1035f296b9d9402abddd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633025"
---
# <a name="output-element-msbuild"></a>Elemento Output (MSBuild)

Armazena valores de saída da tarefa em itens e propriedades.

 \<Project> \<Target>
 \<Task>
 \<Output>

## <a name="syntax"></a>Sintaxe

```xml
<Output TaskParameter="Parameter"
    PropertyName="PropertyName"
    Condition = "'String A' == 'String B'" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`TaskParameter`|Atributo obrigatório.<br /><br /> O nome do parâmetro de saída da tarefa.|
|`PropertyName`|O atributo `PropertyName` ou `ItemName` é necessário.<br /><br /> A propriedade que recebe o valor do parâmetro de saída da tarefa. Seu projeto pode, então, referenciar a propriedade com a sintaxe $ ( \<PropertyName> ). Esse nome de propriedade pode ser um novo nome de propriedade ou um nome que já esteja definido no projeto.<br /><br /> Este atributo não poderá ser usado se `ItemName` também estiver sendo usado.|
|`ItemName`|O atributo `PropertyName` ou `ItemName` é necessário.<br /><br /> O item que recebe o valor do parâmetro de saída da tarefa. Seu projeto pode, então, fazer referência ao item com a sintaxe @ ( \<ItemName> ). O nome do item pode ser um novo nome de item ou um nome que já esteja definido no projeto. Quando o nome do item é um item existente, os valores de parâmetro de saída são adicionados ao item existente. <br /><br /> Este atributo não poderá ser usado se `PropertyName` também estiver sendo usado.|
|`Condition`|Atributo opcional.<br /><br /> Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementos filho

 Nenhum.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Tarefa](../msbuild/task-element-msbuild.md) | Cria e executa uma instância de uma tarefa do MSBuild. |

## <a name="example"></a>Exemplo

 O exemplo de código a seguir mostra uma tarefa `Csc` executada dentro de um elemento `Target`. Os itens e as propriedades passados para os parâmetros da tarefa são declarados fora do escopo deste exemplo. O valor do parâmetro de saída `OutputAssembly` é armazenado no item `FinalAssemblyName` e o valor do parâmetro de saída `BuildSucceeded` é armazenado na propriedade `BuildWorked`. Para obter mais informações, consulte [Tarefas](../msbuild/msbuild-tasks.md).

```xml
<Target Name="Compile" DependsOnTargets="Resources">
    <Csc  Sources="@(CSFile)"
            TargetType="library"
            Resources="@(CompiledResources)"
            EmitDebugInformation="$(includeDebugInformation)"
            References="@(Reference)"
            DebugType="$(debuggingType)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
        <Output TaskParameter="BuildSucceeded"
                  PropertyName="BuildWorked" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Confira também

- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [Tarefas](../msbuild/msbuild-tasks.md)

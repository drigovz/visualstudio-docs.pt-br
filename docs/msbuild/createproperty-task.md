---
title: Tarefa CreateProperty | Microsoft Docs
description: Use a tarefa CreateProperty do MSBuild para preencher propriedades com os valores passados, permitindo que os valores sejam copiados de uma propriedade ou cadeia de caracteres para outra.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d7dd8d7f5a50998832a8fac6f47bf66e9a6bbe9
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796181"
---
# <a name="createproperty-task"></a>Tarefa CreateProperty

Popula as propriedades com os valores passados. Isso permite que os valores sejam copiados de uma propriedade ou cadeia de caracteres para outra.

## <a name="attributes"></a>Atributos

A tabela a seguir descreve os parâmetros da tarefa `CreateProperty`.

| Parâmetro | Descrição |
|------------------| - |
| `Value` | Parâmetro de saída `String` opcional.<br /><br /> Especifica o valor a ser copiado para a nova propriedade. |
| `ValueSetByTask` | Parâmetro de saída `String` opcional.<br /><br /> Contém o mesmo valor que o parâmetro `Value`. Use esse parâmetro somente quando desejar evitar que a propriedade de saída seja definida pelo MSBuild quando ignorar o destino delimitador porque as saídas estão atualizadas. |

## <a name="remarks"></a>Comentários

Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

O exemplo a seguir usa a tarefa `CreateProperty` para criar a propriedade `NewFile` usando a combinação dos valores das propriedades `SourceFilename` e `SourceFileExtension`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <SourceFilename>Module1</SourceFilename>
        <SourceFileExtension>vb</SourceFileExtension>
    </PropertyGroup>

    <Target Name="CreateProperties">

        <CreateProperty
            Value="$(SourceFilename).$(SourceFileExtension)">
            <Output
                TaskParameter="Value"
                PropertyName="NewFile" />
        </CreateProperty>

    </Target>

</Project>
```

Depois de executar o projeto, o valor da propriedade `NewFile` será *Module1.vb* .

## <a name="see-also"></a>Veja também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Tarefas](../msbuild/msbuild-tasks.md)

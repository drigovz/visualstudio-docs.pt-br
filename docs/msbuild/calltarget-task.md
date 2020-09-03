---
title: Tarefa CallTarget | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d29c236b89172ab6dc456be97016b98f2cae19
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094555"
---
# <a name="calltarget-task"></a>Tarefa CallTarget

Invoca os destinos especificados no arquivo de projeto.

## <a name="task-parameters"></a>Parâmetros de tarefa

 A tabela a seguir descreve os parâmetros da tarefa `CallTarget`.

| Parâmetro | Descrição |
|---------------------------| - |
| `RunEachTargetSeparately` | Parâmetro de entrada de `Boolean` opcional.<br /><br /> Se `true` , o mecanismo do MSBuild será chamado uma vez por destino. Se `false` , o mecanismo do MSBuild será chamado uma vez para compilar todos os destinos. O valor padrão é `false`. |
| `TargetOutputs` | Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém as saídas de todos os destinos compilados. |
| `Targets` | Parâmetro `String[]` opcional.<br /><br /> Especifica o destino ou os destinos que serão compilados. |
| `UseResultsCache` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, o resultado em cache será retornado, se presente.<br /><br /> **Observação** Quando uma tarefa MSBuild for executada, a saída é armazenada em cache em um escopo (ProjectFileName, GlobalProperties)[TargetNames] como uma lista de itens de build. |

## <a name="remarks"></a>Comentários

 Se um destino especificado em `Targets` falhar e `RunEachTargetSeparately` for `true`, a tarefa continuará a compilar os destinos restantes.

 Caso deseje criar os destinos padrão, use a [tarefa MSBuild](../msbuild/msbuild-task.md) e defina o parâmetro `Projects` como igual a `$(MSBuildProjectFile)`.

Ao usar `CallTarget` o, o MSBuild avalia o destino chamado em um novo escopo, em oposição ao mesmo escopo do qual ele é chamado. Isso significa que qualquer alteração de item e propriedade no destino chamado não é visível para o destino de chamada.  Para passar informações para o destino de chamada, use o `TargetOutputs` parâmetro de saída.

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

 O exemplo a seguir chama `TargetA` de dentro de `CallOtherTargets`.

```xml
<Project DefaultTargets="CallOtherTargets"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CallOtherTargets">
        <CallTarget Targets="TargetA"/>
    </Target>

    <Target Name="TargetA">
        <Message Text="Building TargetA..." />
    </Target>

</Project>
```

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Destinos](../msbuild/msbuild-targets.md)

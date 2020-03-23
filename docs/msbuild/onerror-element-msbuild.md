---
title: Elemento OnError (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18edfe06a4f2cb98fcb41e93c920b03c53daea8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633077"
---
# <a name="onerror-element-msbuild"></a>Elemento OnError (MSBuild)

Faz com que um ou mais destinos sejam executados se o atributo `ContinueOnError` for `false` para uma tarefa com falha.

 \<Project> \<Target> \<OnError>

## <a name="syntax"></a>Sintaxe

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Condition`|Atributo opcional.<br /><br /> Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Atributo obrigatório.<br /><br /> Os destinos que serão executados se uma tarefa falhar. Separe vários destinos com ponto e vírgula. Vários destinos são executados na ordem especificada.|

### <a name="child-elements"></a>Elementos filho

 Nenhum.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Destino](../msbuild/target-element-msbuild.md) | Elemento de contêiner para tarefas MSBuild. |

## <a name="remarks"></a>Comentários

 O MSBuild `OnError` executa o `Target` elemento se uma das `ContinueOnError` tarefas `ErrorAndStop` do `false`elemento falhar com o atributo definido para (ou ). Quando a tarefa falhar, os destinos especificados no atributo `ExecuteTargets` serão executados. Se houver mais de um elemento `OnError` no destino, os elementos `OnError` serão executados sequencialmente quando a tarefa falhar.

 Para obter `ContinueOnError` informações sobre o atributo, consulte [Elemento tarefa (MSBuild)](../msbuild/task-element-msbuild.md). Para obter mais informações sobre os destinos, consulte [Destinos](../msbuild/msbuild-targets.md).

## <a name="example"></a>Exemplo

 O código a seguir executa as tarefas `TaskOne` e `TaskTwo`. Se `TaskOne` falhar, o MSBuild avalia `OnError` o `OtherTarget` elemento e executa o destino.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>Confira também

- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [Destinos](../msbuild/msbuild-targets.md)

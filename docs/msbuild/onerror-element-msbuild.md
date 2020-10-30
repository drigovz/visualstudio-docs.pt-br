---
title: Elemento OnError (MSBuild) | Microsoft Docs
description: Saiba como o MSBuild usa o elemento OnError para fazer com que um ou mais destinos sejam executados, se o atributo ContinueOnError for false para uma tarefa com falha.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c3793dddf62f67d1c2ff75d8df863dadfdadb7a1
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048943"
---
# <a name="onerror-element-msbuild"></a>Elemento OnError (MSBuild)

Faz com que um ou mais destinos sejam executados se o atributo `ContinueOnError` for `false` para uma tarefa com falha.

 \<Project> \<Target>
 \<OnError>

## <a name="syntax"></a>Syntax

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

 nenhuma.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Target (destino)](../msbuild/target-element-msbuild.md) | Elemento contêiner para tarefas do MSBuild. |

## <a name="remarks"></a>Comentários

 O MSBuild executa o `OnError` elemento se uma das `Target` tarefas do elemento falhar com o `ContinueOnError` atributo definido como `ErrorAndStop` (ou `false` ). Quando a tarefa falhar, os destinos especificados no atributo `ExecuteTargets` serão executados. Se houver mais de um elemento `OnError` no destino, os elementos `OnError` serão executados sequencialmente quando a tarefa falhar.

 Para obter informações sobre o `ContinueOnError` atributo, consulte [elemento Task (MSBuild)](../msbuild/task-element-msbuild.md). Para obter mais informações sobre os destinos, consulte [Destinos](../msbuild/msbuild-targets.md).

## <a name="example"></a>Exemplo

 O código a seguir executa as tarefas `TaskOne` e `TaskTwo`. Se `TaskOne` falhar, o MSBuild avaliará o `OnError` elemento e executará o `OtherTarget` destino.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>Veja também

- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [Destinos](../msbuild/msbuild-targets.md)

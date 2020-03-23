---
title: Elemento ParameterGroup| Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c06b9c530d3fff0fdfa429df633daaa4dde8c52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263065"
---
# <a name="parametergroup-element"></a>Elemento ParameterGroup

Contém uma lista opcional de parâmetros que estarão `UsingTask` `TaskFactory`presentes na tarefa gerada por um . Para obter mais informações, consulte [O elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<ParameterGroup>

## <a name="syntax"></a>Sintaxe

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

 Nenhum.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Parâmetro](../msbuild/parameter-element.md)|Contém informações sobre um parâmetro específico de uma tarefa que é gerada por um `UsingTask` `TaskFactory`. O nome do elemento é o nome do parâmetro.|

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Fornece uma maneira de registrar tarefas no MSBuild. Pode ser que não haja nenhum ou mais de um elemento `UsingTask` em um projeto. |

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como usar o elemento `ParameterGroup`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)

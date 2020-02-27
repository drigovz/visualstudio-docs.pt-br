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
ms.openlocfilehash: 28d6def203a819d41a420899663d1a974612c631
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632986"
---
# <a name="parametergroup-element"></a>Elemento ParameterGroup

Contém uma lista opcional de parâmetros que estarão presentes na tarefa que é gerada por um `UsingTask` `TaskFactory`. Para saber mais, confira [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<ParameterGroup>

## <a name="syntax"></a>Sintaxe

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.

### <a name="attributes"></a>Atributos

 Nenhum.

### <a name="child-elements"></a>Elementos filho

|Elemento|DESCRIÇÃO|
|-------------|-----------------|
|[Parâmetro](../msbuild/parameter-element.md)|Contém informações sobre um parâmetro específico para uma tarefa que é gerada por um `UsingTask` `TaskFactory`. O nome do elemento é o nome do parâmetro.|

### <a name="parent-elements"></a>Elementos pai

| Elemento | DESCRIÇÃO |
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
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Referência de esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)

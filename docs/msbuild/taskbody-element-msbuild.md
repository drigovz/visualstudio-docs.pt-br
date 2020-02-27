---
title: Elemento TaskBody (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45b255f782390cfc478ac2f7bce58170e4e2b268
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631830"
---
# <a name="taskbody-element-msbuild"></a>Elemento TaskBody (MSBuild)

Contém os dados que são passados para um `TaskFactory`de `UsingTask`. Para saber mais, confira [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<TaskBody>

## <a name="syntax"></a>Sintaxe

```xml
<TaskBody Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|DESCRIÇÃO|
|---------------|-----------------|
|`Evaluate`|Atributo booliano opcional.<br /><br /> Se `true`, MSBuild avalia todos os elementos internos e expande os itens e propriedades antes de transmitir as informações para o `TaskFactory`, quando a tarefa é instanciada.|

### <a name="child-elements"></a>Elementos filho

|Elemento|DESCRIÇÃO|
|-------------|-----------------|
|data|O texto entre as `TaskBody` marcas é enviada textual para `TaskFactory`.|

### <a name="parent-elements"></a>Elementos pai

| Elemento | DESCRIÇÃO |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Fornece uma maneira de registrar tarefas no MSBuild. Pode ser que não haja nenhum ou mais de um elemento `UsingTask` em um projeto. |

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como usar o elemento `TaskBody` com um atributo `Evaluate`.

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

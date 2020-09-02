---
title: Elemento Task de UsingTask (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36644a6b21092361d92dba5f0886eb4198884995
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78263182"
---
# <a name="task-element-of-usingtask-msbuild"></a>Elemento Task de UsingTask (MSBuild)

Contém os dados que são passados para um `UsingTask` `TaskFactory`. Para obter mais informações, consulte [elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<Task>

## <a name="syntax"></a>Syntax

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Evaluate`|Atributo booliano opcional.<br /><br /> Se `true`, MSBuild avalia todos os elementos internos e expande os itens e propriedades antes de transmitir as informações para o `TaskFactory`, quando a tarefa é instanciada.|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Dados|O texto entre as `Task` marcas é enviada textual para `TaskFactory`.|

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Fornece uma maneira de registrar tarefas no MSBuild. Pode ser que não haja nenhum ou mais de um elemento `UsingTask` em um projeto. |

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como usar o elemento `Task` com um atributo `Evaluate`.

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

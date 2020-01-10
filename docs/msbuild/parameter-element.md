---
title: Elemento de parâmetro| Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d1351f47ec8acc5aa5a510ede9c2284ec97c248
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590456"
---
# <a name="parameter-element"></a>Elemento Parameter
Contém informações sobre um parâmetro específico para uma tarefa que é gerada por um `UsingTask` `TaskFactory`.  O nome do elemento é o nome do parâmetro.  Para saber mais, confira [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<ParameterGroup> \<Parameter>

## <a name="syntax"></a>Sintaxe

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.

### <a name="attributes"></a>{1&gt;{2&gt;Atributos&lt;2}&lt;1}

|Atributo|Descrição|
|---------------|-----------------|
|`ParameterType`|Atributo opcional.<br /><br /> O tipo .NET do parâmetro, por exemplo, `System.String`.|
|`Output`|Atributo booliano opcional.<br /><br /> Se `true`, esse parâmetro será um parâmetro de saída para a tarefa. Por padrão, o valor é `false`.|
|`Required`|Atributo booliano opcional.<br /><br /> Se `true`, esse parâmetro será um parâmetro necessário para a tarefa. Por padrão, o valor é `false`.|

### <a name="child-elements"></a>Child elements
 Nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contém uma lista opcional de parâmetros que estarão presentes na tarefa que é gerada por um `UsingTask` `TaskFactory`.|

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra como usar o elemento `Parameter`.

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

## <a name="see-also"></a>Veja também
- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Referência de esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)

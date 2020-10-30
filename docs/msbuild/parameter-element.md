---
title: Elemento de parâmetro| Microsoft Docs
description: Saiba mais sobre o elemento Parameter do MSBuild, que contém informações sobre um parâmetro específico para uma tarefa gerada por um UsingTask TaskFactory.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e7aa8809cbce8f07e18666afb1734026fdc9694b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048876"
---
# <a name="parameter-element"></a>Elemento Parameter

Contém informações sobre um parâmetro específico de uma tarefa que é gerada por um `UsingTask` `TaskFactory`.  O nome do elemento é o nome do parâmetro.  Para obter mais informações, consulte [elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>
 \<Parameter>

## <a name="syntax"></a>Syntax

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`ParameterType`|Atributo opcional.<br /><br /> O tipo .NET do parâmetro, por exemplo, `System.String`.|
|`Output`|Atributo booliano opcional.<br /><br /> Se `true`, esse parâmetro será um parâmetro de saída para a tarefa. Por padrão, o valor é `false`.|
|`Required`|Atributo booliano opcional.<br /><br /> Se `true`, esse parâmetro será um parâmetro necessário para a tarefa. Por padrão, o valor é `false`.|

### <a name="child-elements"></a>Elementos filho

 nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contém uma lista opcional de parâmetros que estarão presentes na tarefa que é gerada por um `UsingTask` `TaskFactory` .|

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como usar o elemento `Parameter`.

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

## <a name="see-also"></a>Veja também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)

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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a531073ba6f2f55272b719a116caad724d29e53
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916157"
---
# <a name="parametergroup-element"></a>Elemento ParameterGroup
Contém uma lista opcional de parâmetros que estarão presentes na tarefa que é gerada por um `UsingTask` `TaskFactory`. Para saber mais, confira [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  

## <a name="syntax"></a>Sintaxe  

```xml  
<ParameterGroup />  
```  

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  
 nenhuma.  

### <a name="child-elements"></a>Elementos filho  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Parâmetro](../msbuild/parameter-element.md)|Contém informações sobre um parâmetro específico de uma tarefa que é gerada por um `UsingTask` `TaskFactory`. O nome do elemento é o nome do parâmetro.|  

### <a name="parent-elements"></a>Elementos pai  

| Elemento | Descrição |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Fornece uma maneira para registrar tarefas em [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Pode ser que não haja nenhum ou mais de um elemento `UsingTask` em um projeto. |

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

## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Referência de esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)

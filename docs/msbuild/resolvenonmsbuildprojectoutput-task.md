---
title: Tarefa ResolveNonMSBuildProjectOutput | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a482e93bb2a4e03eac7d4b0188303f203ea05445
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013880"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>Tarefa ResolveNonMSBuildProjectOutput
Determina os arquivos de saída para referências de projeto não MSBuild.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `ResolveNonMSBuildProjectOutput`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Parâmetro `String` opcional.<br /><br /> Especifica uma cadeia de caracteres XML que contém saídas de projeto resolvidas.|  
|`ProjectReferences`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica as referências do projeto.|  
|`ResolvedOutputPaths`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém a lista de caminhos de referência resolvidos (e preserva os atributos de referência do projeto original).|  
|`UnresolvedProjectReferences`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém a lista de itens de referência de projeto que não puderam ser resolvidos usando a lista pré-resolvida de saídas.<br /><br /> Como o Visual Studio só pré-resolve projetos não MSBuild, isso significa que as referências de projeto nesta lista estão no formato MSBuild.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
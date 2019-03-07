---
title: Tarefa GenerateTrustInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f1cf52286de97980eb269c3b52055be4455c38d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54790146"
---
# <a name="generatetrustinfo-task"></a>Tarefa GenerateTrustInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Gera a confiança do aplicativo do manifesto base e dos parâmetros `TargetZone` e `ExcludedPermissions`.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `GenerateTrustInfo`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`ApplicationDependencies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os assemblies dependentes.|  
|`BaseManifest`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o manifesto base do qual gerar a confiança do aplicativo.|  
|`ExcludedPermissions`|Parâmetro `String` opcional.<br /><br /> Especifica um ou mais valores de identidade de permissão separados por ponto e vírgula a serem excluídos do conjunto de permissões da zona padrão.|  
|`TargetZone`|Parâmetro `String` opcional.<br /><br /> Especifica um conjunto de permissões padrão de zona, que é obtido da política do computador.|  
|`TrustInfoFile`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem> necessário.<br /><br /> Especifica o arquivo que contém as informações de confiança de segurança do aplicativo.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)

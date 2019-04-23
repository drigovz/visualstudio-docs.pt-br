---
title: Tarefa UpdateManifest | Microsoft Docs
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
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e2ec8a0cd854a04c338add22c3f90daf0bf14ba
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656993"
---
# <a name="updatemanifest-task"></a>Tarefa UpdateManifest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atualiza as propriedades selecionadas em um manifesto e assina-as novamente.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `UpdateManifest`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`ApplicationManifest`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o manifesto do aplicativo.|  
|`ApplicationPath`|Parâmetro `String` obrigatório.<br /><br /> Especifica o caminho do manifesto do aplicativo.|  
|`InputManifest`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o manifesto a atualizar.|  
|`OutputManifest`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o manifesto que contém propriedades atualizadas.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados na tabela, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Tarefa de Classe Base](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)

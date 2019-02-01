---
title: Tarefa XslTransformation | Microsoft Docs
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
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 892ecb7f97be3d89a0f6e8104b0b55647a6fe63e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793126"
---
# <a name="xsltransformation-task"></a>Tarefa XslTransformation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Transformações um XML de entrada usando um XSLT ou XSLT compilado e saídas para um arquivo ou um dispositivo de saída.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `XslTransformation`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`OutputPaths`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos de saída para a transformação XML.|  
|`Parameters`|Parâmetro `String` opcional.<br /><br /> Especifica os parâmetros para o documento de entrada XSLT.|  
|`XmlContent`|Parâmetro `String` opcional.<br /><br /> Especifica a entrada XML como uma cadeia de caracteres.|  
|`XmlInputPaths`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os arquivos de entrada XML.|  
|`XslCompiledDllPath`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o XSLT compilado.|  
|`XslContent`|Parâmetro `String` opcional.<br /><br /> Especifica a entrada XSLT como uma cadeia de caracteres.|  
|`XslInputPath`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o arquivo de entrada XSLT.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)

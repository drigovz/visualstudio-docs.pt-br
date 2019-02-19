---
title: Tarefa FormatVersion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fbd03676d69dde5f9a6d169739a25e7b5e1b82e
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54755119"
---
# <a name="formatversion-task"></a>Tarefa FormatVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Acrescenta o número de revisão ao número de versão.  
  
-   Caso #1: Entrada: Version=\<undefined>;  Revision=\<don't care>;   Saída: OutputVersion="1.0.0.0"  
  
-   Caso #2: Entrada: Version="1.0.0.*"  Revision="5"  Saída: OutputVersion="1.0.0.5"  
  
-   Caso #3: Entrada: Version="1.0.0.0"  Revision=\<don't care>;  Saída: OutputVersion="1.0.0.0"  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `FormatVersion`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`FormatType`|Parâmetro `String` opcional.<br /><br /> Especifica o tipo do formato.<br /><br /> -"Versão" = versão.<br />-   "Path" = substituir "." por "_";|  
|`OutputVersion`|Parâmetro de saída `String` opcional.<br /><br /> Especifica a versão de saída que inclui o número de revisão.|  
|`Revision`|Parâmetro `Int32` opcional.<br /><br /> Especifica a revisão a ser acrescentada à versão.|  
|`Version`|Parâmetro `String` opcional.<br /><br /> Especifica a cadeia de caracteres do número de versão para o formato.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)

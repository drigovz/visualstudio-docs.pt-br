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
ms.openlocfilehash: ee6e163bd6587d93c970a56ac1c08383084ddc0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149622"
---
# <a name="formatversion-task"></a>Tarefa FormatVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Acrescenta o número de revisão ao número de versão.  
  
- #1 de caso: entrada: versão = \<undefined> ;  Revisão = \<don't care> ;   Saída: OutputVersion = "1.0.0.0"  
  
- Caso #2: Entrada: Version="1.0.0.*"  Revision="5"  Saída: OutputVersion="1.0.0.5"  
  
- #3 de caso: entrada: versão = "1.0.0.0" revisão = \<don't care> ;  Saída: OutputVersion = "1.0.0.0"  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `FormatVersion`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`FormatType`|Parâmetro `String` opcional.<br /><br /> Especifica o tipo do formato.<br /><br /> -"Versão" = versão.<br />-   "Path" = substituir "." por "_";|  
|`OutputVersion`|Parâmetro de saída `String` opcional.<br /><br /> Especifica a versão de saída que inclui o número de revisão.|  
|`Revision`|Parâmetro `Int32` opcional.<br /><br /> Especifica a revisão a ser acrescentada à versão.|  
|`Version`|Parâmetro `String` opcional.<br /><br /> Especifica a cadeia de caracteres do número de versão para o formato.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Tarefa](../msbuild/msbuild-tasks.md)   
 [Referência de tarefa](../msbuild/msbuild-task-reference.md)

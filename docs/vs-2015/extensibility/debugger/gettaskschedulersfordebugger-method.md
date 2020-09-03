---
title: Método GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 995bf40669a4480f6f1ddfe8071a7885a4659c9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152720"
---
# <a name="gettaskschedulersfordebugger-method"></a>Método GetTaskSchedulersForDebugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler> objetos que estão ativos no momento.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (no mscorlib.dll)  
  
 Como você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valor retornado  
 Uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler> objetos que estão atualmente ativos neste <xref:System.AppDomain> .  
  
## <a name="remarks"></a>Comentários  
 Esse método não é thread-safe e não deve ser usado simultaneamente com outras instâncias do <xref:System.Threading.Tasks.TaskScheduler> . Ele deve ser chamado a partir de um depurador somente quando o depurador tiver suspenso todos os outros threads.  
  
## <a name="see-also"></a>Consulte Também  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)

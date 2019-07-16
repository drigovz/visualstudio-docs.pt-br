---
title: Encerramento e desanexação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92fe88826baf19ba66b200990aee7797e91f87b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68176676"
---
# <a name="termination-and-detaching"></a>Término e desconexão
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O exemplo a seguir descreve um encerramento normal.  
  
## <a name="discussion"></a>Discussão  
 Após o [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interface continua, se não houver nenhum pontos de interrupção, exceções, erros de tempo de execução ou loops infinitos no aplicativo a ser depurado, o programa que está sendo depurado será executado até a conclusão. Este é um encerramento normal.  
  
 Você deve enviar uma [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) para implementar um encerramento normal. Isso requer a implementação de [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

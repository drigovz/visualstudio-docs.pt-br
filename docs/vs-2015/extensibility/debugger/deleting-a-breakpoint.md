---
title: Excluindo um ponto de interrupção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409403"
---
# <a name="deleting-a-breakpoint"></a>Excluindo um ponto de interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O exemplo a seguir descreve o processo ao excluir um ponto de interrupção pendente:  
  
## <a name="deletion-process"></a>Processo de exclusão  
 O Gerenciador de sessão de depuração (SDM) chama o [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) método para remover o ponto de interrupção pendente e acoplados todos os pontos de interrupção associado dele.  
  
> [!NOTE]
> Também é possível excluir um único ponto de interrupção associado por uma chamada para [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)

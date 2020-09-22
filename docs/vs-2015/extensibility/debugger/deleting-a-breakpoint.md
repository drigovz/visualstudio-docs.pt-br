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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838492"
---
# <a name="deleting-a-breakpoint"></a>Excluindo um ponto de interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O seguinte descreve o processo ao excluir um ponto de interrupção pendente:  
  
## <a name="deletion-process"></a>Processo de exclusão  
 O SDM (Gerenciador de depuração de sessão) chama o método [IDebugPendingBreakpoint2::D xcluir](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) para remover o ponto de interrupção pendente e todos os pontos de interrupção associados a ele.  
  
> [!NOTE]
> Um ponto de interrupção de associação simples também pode ser excluído por uma chamada para [IDebugBoundBreakpoint2::D xcluir](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Chamando eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)

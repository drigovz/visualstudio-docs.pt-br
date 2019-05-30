---
title: Excluindo um ponto de interrupção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7551ee12993780544bbb9c9eb127a9bfb4364e8d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345825"
---
# <a name="deleting-a-breakpoint"></a>Excluindo um ponto de interrupção
O exemplo a seguir descreve o processo ao excluir um ponto de interrupção pendente:

## <a name="deletion-process"></a>Processo de exclusão
 O Gerenciador de sessão de depuração (SDM) chama o [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) método para remover o ponto de interrupção pendente e acoplados todos os pontos de interrupção associado dele.

> [!NOTE]
> Também é possível excluir um único ponto de interrupção associado por uma chamada para [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Consulte também
- [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
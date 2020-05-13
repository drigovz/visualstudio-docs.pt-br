---
title: Excluindo um Breakpoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77be200a11eb7b3985a4c1a47e4cddaa543f900
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738944"
---
# <a name="deleting-a-breakpoint"></a>Excluindo um ponto de ruptura
O seguinte descreve o processo ao excluir um ponto de ruptura pendente:

## <a name="deletion-process"></a>Processo de exclusão
 O SDM (Session Debug Manager, gerenciador de depuração de sessão) chama o [método IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) para remover o breakpoint pendente e todos os pontos de interrupção vinculados vinculados a partir dele.

> [!NOTE]
> Um único ponto de ruptura vinculado também pode ser excluído por uma chamada para [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Confira também
- [Eventos de depurador de chamadas](../../extensibility/debugger/calling-debugger-events.md)

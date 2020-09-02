---
title: Excluindo um ponto de interrupção | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738944"
---
# <a name="deleting-a-breakpoint"></a>Excluindo um ponto de interrupção
O seguinte descreve o processo ao excluir um ponto de interrupção pendente:

## <a name="deletion-process"></a>Processo de exclusão
 O SDM (Gerenciador de depuração de sessão) chama o método [IDebugPendingBreakpoint2::D xcluir](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) para remover o ponto de interrupção pendente e todos os pontos de interrupção associados a ele.

> [!NOTE]
> Um ponto de interrupção de associação simples também pode ser excluído por uma chamada para [IDebugBoundBreakpoint2::D xcluir](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Confira também
- [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)

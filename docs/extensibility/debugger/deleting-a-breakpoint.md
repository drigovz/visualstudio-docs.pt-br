---
title: Excluindo um ponto de interrupção | Microsoft Docs
description: Saiba como o Gerenciador de depuração de sessão remove um ponto de interrupção pendente e todos os pontos de interrupção associados a ele quando um ponto de interrupção pendente é excluído.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ebd2922f48a53c371f4930e5de1fd86ed6852a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862169"
---
# <a name="deleting-a-breakpoint"></a>Excluindo um ponto de interrupção
O seguinte descreve o processo ao excluir um ponto de interrupção pendente:

## <a name="deletion-process"></a>Processo de exclusão
 O SDM (Gerenciador de depuração de sessão) chama o método [IDebugPendingBreakpoint2::D xcluir](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) para remover o ponto de interrupção pendente e todos os pontos de interrupção associados a ele.

> [!NOTE]
> Um ponto de interrupção de associação simples também pode ser excluído por uma chamada para [IDebugBoundBreakpoint2::D xcluir](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Consulte também
- [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)

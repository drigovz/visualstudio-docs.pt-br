---
title: Erros de ponto de interrupção | Microsoft Docs
description: Saiba mais sobre o processo quando um ponto de interrupção tenta se associar ao código, mas falha e como solucionar problemas de erros de ponto de interrupção.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 840fde5943cb2249bdf73cc92ca15878ae4e3890
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943448"
---
# <a name="breakpoint-errors"></a>Erros de ponto de interrupção
O a seguir descreve o processo quando um ponto de interrupção tenta se associar ao código, mas falha.

## <a name="troubleshoot-a-breakpoint-error"></a>Solucionar um erro de ponto de interrupção

1. O mecanismo de depuração (DE) envia um [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) para o SDM (Gerenciador de depuração de sessão).

2. O SDM chama [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) para obter o ponto de interrupção de erro.

3. O SDM chama [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) para obter o ponto de interrupção pendente do qual o ponto de interrupção de erro foi originado.

4. O SDM chama [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) para obter o motivo pelo qual o ponto de interrupção de erro falhou ao associar.

## <a name="see-also"></a>Confira também
- [Chamando eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)

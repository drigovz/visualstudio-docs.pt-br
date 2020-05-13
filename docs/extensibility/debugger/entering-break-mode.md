---
title: Entrando no modo break | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bbcec8adf6468f70d95df5f291ce1e5540406cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738885"
---
# <a name="enter-break-mode"></a>Insira o modo de quebra
As informações a seguir descrevem o processo que ocorre quando um ponto de ruptura é encontrado depois de entrar em uma função, correr para a linha de código-fonte que tem o cursor nele ou correr para um ponto de ruptura.

## <a name="break-mode-process"></a>Processo de modo de quebra

1. O mecanismo de depuração (DE) envia [IDebugBreakpointEvent2,](../../extensibility/debugger/reference/idebugbreakpointevent2.md) [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)ou qualquer outro evento de parada para fazer com que o IDE entre no modo de quebra.

2. O SDM obtém as informações da pilha de chamadas do segmento, da seguinte forma:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obter as informações do código-fonte

    - [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) para obter o nome do arquivo

    - [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) para obter o intervalo de demonstrações

    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) para obter informações de memória

## <a name="see-also"></a>Confira também
- [Chamando eventos de depurador](../../extensibility/debugger/calling-debugger-events.md)

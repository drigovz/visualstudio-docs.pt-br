---
title: Entrar no modo de interrupção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8da96c1df3423665ed223fecdd43007ba5a6e671
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045662"
---
# <a name="enter-break-mode"></a>Insira o modo de interrupção
As informações a seguir descrevem o processo que ocorre quando um ponto de interrupção é encontrado depois de entrar em uma função, em execução para a linha de código-fonte que contém o cursor de ou em execução para um ponto de interrupção.

## <a name="break-mode-process"></a>Processo do modo de interrupção

1. O mecanismo de depuração (DES) envia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), ou qualquer outro evento de interrupção para fazer com que o IDE entrar no modo de interrupção.

2. O SDM obtém as informações de pilha de chamadas do thread, da seguinte maneira:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obter as informações de código fonte

    - [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) para obter o nome do arquivo

    - [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) obter o intervalo de instrução

    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) para obter informações de memória

## <a name="see-also"></a>Consulte também
- [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
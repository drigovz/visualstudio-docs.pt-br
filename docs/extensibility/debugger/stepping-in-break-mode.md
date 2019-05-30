---
title: Passo a passo no modo de interrupção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3a8688f32a97d27ee6f6e2d18fcea8e25feaac2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348541"
---
# <a name="stepping-in-break-mode"></a>Passo a passo no modo de interrupção
A seção a seguir descreve o processo que ocorre quando o depurador está no modo de interrupção e deve percorrer o código:

## <a name="stepping-process"></a>Passo a passo do processo

1. Chame [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) com [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumentos para executar uma etapa.

2. Quando a etapa for concluída, envie uma [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como um evento de interrupção.

## <a name="see-also"></a>Consulte também
- [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
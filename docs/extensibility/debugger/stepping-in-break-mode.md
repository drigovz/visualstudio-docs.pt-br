---
title: Passo a passo no modo de interrupção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb7b7e847c116f3aab38a12ec9801988bb8b3fc1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111539"
---
# <a name="stepping-in-break-mode"></a>Passo a passo no modo de interrupção
A seção a seguir descreve o processo que ocorre quando o depurador está no modo de interrupção e deve percorrer o código:

## <a name="stepping-process"></a>Passo a passo do processo

1. Chame [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) com [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumentos para executar uma etapa.

2. Quando a etapa for concluída, envie uma [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como um evento de interrupção.

## <a name="see-also"></a>Consulte também
- [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
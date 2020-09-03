---
title: Passando no modo de interrupção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3161fc1c1ec8b44d96b3793198ac630ba2e32d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712856"
---
# <a name="stepping-in-break-mode"></a>Passando no modo de interrupção
A seção a seguir descreve o processo que ocorre quando o depurador está no modo de interrupção e deve percorrer o código:

## <a name="stepping-process"></a>Processo de depuração

1. Chame [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) com argumentos [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) para executar uma etapa.

2. Quando a etapa for concluída, envie um [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como um evento de parada.

## <a name="see-also"></a>Confira também
- [Chamando eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)

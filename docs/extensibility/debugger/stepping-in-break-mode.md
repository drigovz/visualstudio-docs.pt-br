---
title: Pisando no Modo Break | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712856"
---
# <a name="stepping-in-break-mode"></a>Pisando no modo de quebra
A seção a seguir descreve o processo que ocorre quando o depurador está no modo de quebra e deve passar pelo código:

## <a name="stepping-process"></a>Processo de etapas

1. Chamada [IDebugProgram2::Passo](../../extensibility/debugger/reference/idebugprogram2-step.md) com argumentos [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) para executar uma etapa.

2. Quando a etapa estiver concluída, envie um [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como um evento de parada.

## <a name="see-also"></a>Confira também
- [Chamando eventos de depurador](../../extensibility/debugger/calling-debugger-events.md)

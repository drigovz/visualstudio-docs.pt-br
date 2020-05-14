---
title: Gerente de depuração de sessão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712879"
---
# <a name="session-debug-manager"></a>Gerente de depuração de sessão
O SDM (Session Debug Manager, gerenciador de depuração) gerencia qualquer número de mecanismos de depuração (DE) que estão depurando qualquer número de programas em vários processos em qualquer número de máquinas. Além de ser um multiplexador do motor de depuração, o SDM fornece uma visão unificada da sessão de depuração para o IDE.

## <a name="session-debug-manager-operation"></a>Operação de gerente de depuração de sessão
 O gerenciador de depuração de sessão (SDM) gerencia o DE. Pode haver mais de um motor de depuração funcionando em uma máquina ao mesmo tempo. Para multiplexar os DEs, o SDM envolve uma série de interfaces dos DEs e as expõe ao IDE como uma única interface.

 Para aumentar o desempenho, algumas interfaces não são multiplexadas. Em vez disso, eles são usados diretamente do DE, e as chamadas para essas interfaces não passam pelo SDM. Por exemplo, as interfaces usadas com contextos de memória, código e documento não são multiplexadas, porque se referem a uma instrução, memória ou documento específico em um programa específico depurado por um DE específico. Nenhum outro DE precisa estar envolvido nesse nível de comunicação.

 Isso não é verdade em todos os contextos. As chamadas para a interface de contexto de avaliação de expressão passam pelo SDM. Durante a avaliação de expressão, o SDM envolve a interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) que ele dá ao IDE porque, quando essa expressão é avaliada, pode envolver vários DEs que estão depurando programas no mesmo processo que podem estar sendo executados no mesmo segmento.

 O SDM normalmente age como um mecanismo de delegação, mas pode funcionar como um mecanismo de transmissão. Por exemplo, durante a avaliação de expressão, o SDM atua como um mecanismo de transmissão para notificar todos os DEs de que eles podem executar código em um segmento especificado. Da mesma forma, quando o SDM recebe um evento de parada, ele transmite para os programas que eles devem parar de executar. Quando um passo é chamado, o SDM transmite para os programas que eles podem continuar a execução. Os pontos de interrupção também são transmitidos para todos os DE.

 O SDM não rastreia o quadro atual do programa, do segmento ou da pilha. As informações de processo, programa e segmento são enviadas ao SDM em conjunto com eventos específicos de depuração.

## <a name="see-also"></a>Confira também
- [Motor de depuração](../../extensibility/debugger/debug-engine.md)
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
- [Contextos de depuração](../../extensibility/debugger/debugger-contexts.md)

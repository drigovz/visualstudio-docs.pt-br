---
title: Fios | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed5c06e0c42dac1f0539cc2c7c5886d95b23ae1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712472"
---
# <a name="threads"></a>Threads
Na arquitetura dedepurador, um *segmento:*

- É a unidade fundamental do cálculo. Um segmento executa sequencialmente suas instruções no contexto de uma única pilha de chamadas, movendo-se de um contexto de código para o outro.

- Pode identificar-se e o programa em que está sendo executado. Os fios podem ser nomeados, suspensos e retomados. Um segmento também pode enumerar seus quadros de pilha associados e, sob algumas condições, pode ser movido para outro quadro de pilha. Dado o contexto de um quadro de pilha, um segmento pode retornar seu segmento lógico associado, se houver. Um segmento tem propriedades, como uma contagem de suspensão, que podem ser exibidas na janela **Threads** do IDE.

- É representado por uma interface [IDebugThread2,](../../extensibility/debugger/reference/idebugthread2.md) normalmente criada por um mecanismo de depuração (DE) ou máquina virtual como conseqüência da execução de um programa.

## <a name="see-also"></a>Confira também
- [Programas](../../extensibility/debugger/programs.md)
- [Quadros de pilha](../../extensibility/debugger/stack-frames.md)
- [Motor de depuração](../../extensibility/debugger/debug-engine.md)
- [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md)
- [Gerente de depuração de sessão](../../extensibility/debugger/session-debug-manager.md)

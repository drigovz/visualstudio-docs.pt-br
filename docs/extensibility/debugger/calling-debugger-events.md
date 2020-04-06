---
title: Chamando eventos de depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 869bd87952aebf8ad640c5aeb439c9e99929f4c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739168"
---
# <a name="call-debugger-events"></a>Eventos de depurador de chamadas
Eventos em sessões de depuração ocorrem em uma ordem específica.

## <a name="discussion"></a>Discussão
 Para entender o padrão de chamadas entre o mecanismo de depuração (DE) e o gerenciador de depuração de sessão (SDM), o seguinte representa a ordem de chamada dos eventos que ocorrem em uma sessão típica de depuração:

1. [Anexando e desprendendo a um programa](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Lançando o depurador](../../extensibility/debugger/launching-the-debugger.md)

3. [Terminando um programa](../../extensibility/debugger/terminating-a-program.md)

4. [Criando um ponto de ruptura](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Quando um ponto de ruptura se liga ou se torna desvinculado](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Erros de ponto de ruptura](../../extensibility/debugger/breakpoint-errors.md)

7. [Atingindo um ponto de interrupção](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Excluindo um ponto de ruptura](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Entrando no modo de quebra](../../extensibility/debugger/entering-break-mode.md)

10. [Pisando no modo de quebra](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Avaliação de expressão no modo de quebra](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Manuseio de exceções](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Confira também
- [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

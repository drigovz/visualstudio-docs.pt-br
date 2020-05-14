---
title: Manipulação de exceções (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738765"
---
# <a name="exception-handling-visual-studio-sdk"></a>Manipulação de exceções (Visual Studio SDK)
O seguinte descreve o processo que ocorre quando exceções são lançadas.

## <a name="exception-handling-process"></a>Processo de manipulação de exceções

1. Quando uma exceção é lançada pela primeira vez, mas antes de ser tratada pelo manipulador de exceção no programa que está sendo depurado, o mecanismo de depuração (DE) envia um [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) para o Gerenciador de depuração de sessão (SDM) como um evento de parada. O `IDebugExceptionEvent2` é enviado se apenas as configurações da exceção (especificadas na caixa de diálogo Exceções no pacote de depuração) especificarem que o usuário deseja parar em notificações de exceção de primeira chance.

2. O SDM chama [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) para obter a propriedade de exceção.

3. O pacote de depuração chama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar quais opções apresentar ao usuário.

4. O pacote de depuração pergunta ao usuário como lidar com a exceção abrindo uma caixa de diálogo de exceção de primeira chance.

5. Se o usuário optar por continuar, o SDM chamará [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Se o método retornar S_OK, [chamaria IDebugExceptionEvent2::PassToDebugge](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         -ou-

         Se o método retornar S_FALSE, o programa que está sendo depurado recebe uma segunda chance de lidar com a exceção.

6. Se o programa que está sendo depurado não tiver nenhum `IDebugExceptionEvent2` manipulador para uma exceção de segunda chance, o DE envia um para o SDM como **EVENT_SYNC_STOP**.

7. O pacote de depuração pergunta ao usuário como lidar com a exceção abrindo uma caixa de diálogo de exceção de primeira chance.

8. O pacote de depuração chama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar quais opções apresentar ao usuário.

9. O pacote de depuração pergunta ao usuário como lidar com a exceção abrindo uma caixa de diálogo de exceção de segunda chance.

10. Se o método retornar `IDebugExceptionEvent2::PassToDebuggee`S_OK, chamadas .

## <a name="see-also"></a>Confira também
- [Eventos de depurador de chamadas](../../extensibility/debugger/calling-debugger-events.md)

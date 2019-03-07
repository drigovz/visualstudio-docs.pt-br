---
title: (Visual Studio SDK) de tratamento de exceções | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b580a4774cfe06f81e2d9798ef6cf949afe8c1c8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710845"
---
# <a name="exception-handling-visual-studio-sdk"></a>Tratamento de exceção (SDK do Visual Studio)
O exemplo a seguir descreve o processo que ocorre quando as exceções são geradas.

## <a name="exception-handling-process"></a>Processo de manipulação de exceção

1.  Quando uma exceção é lançada pela primeira vez, mas antes que ela é tratada pelo manipulador de exceção no programa que está sendo depurado, o mecanismo de depuração (DES) envia uma [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) para o Gerenciador de depuração de sessão (SDM) como um evento de interrupção. O `IDebugExceptionEvent2` é enviado se apenas as configurações para a exceção (especificada na caixa de diálogo exceções no pacote de depuração) especificam que o usuário deseja parar em notificações de exceção de primeira chance.

2.  As chamadas SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) para obter a propriedade de exceção.

3.  As chamadas de pacote de depuração [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar as opções para apresentar ao usuário.

4.  O pacote de depuração pede ao usuário como lidar com a exceção, abrindo uma caixa de diálogo de exceção de primeira chance.

5.  Se o usuário optar por continuar, o SDM chama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    -   Se o método retorna S_OK, chama [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         -ou-

         Se o método retorna S_FALSE, o programa que está sendo depurado recebe uma segunda chance para tratar a exceção.

6.  Se o programa que está sendo depurado não tem nenhum manipulador para uma exceção de segunda chance, o DE envia um `IDebugExceptionEvent2` para o SDM como **EVENT_SYNC_STOP**.

7.  O pacote de depuração pede ao usuário como lidar com a exceção, abrindo uma caixa de diálogo de exceção de primeira chance.

8.  As chamadas de pacote de depuração [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar as opções para apresentar ao usuário.

9. O pacote de depuração pede ao usuário como lidar com a exceção, abrindo uma caixa de diálogo de exceção de segunda chance.

10. Se o método retorna S_OK, chama `IDebugExceptionEvent2::PassToDebuggee`.

## <a name="see-also"></a>Consulte também
- [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
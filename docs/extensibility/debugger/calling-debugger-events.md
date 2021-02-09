---
title: Chamando eventos do depurador | Microsoft Docs
description: Eventos em sessões de depuração ocorrem em uma ordem específica. Este artigo lista a ordem de chamada dos eventos que ocorrem em uma sessão de depuração típica.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ef1aad17caae12b046ac483808f847a6e186792
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930701"
---
# <a name="call-debugger-events"></a>Chamar eventos do depurador
Eventos em sessões de depuração ocorrem em uma ordem específica.

## <a name="discussion"></a>Discussão
 Para entender o padrão de chamadas entre o mecanismo de depuração (DE) e o SDM (Gerenciador de depuração de sessão), o seguinte representa a ordem de chamada dos eventos que ocorrem em uma sessão de depuração típica:

1. [Anexando e desanexando a um programa](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Iniciando o depurador](../../extensibility/debugger/launching-the-debugger.md)

3. [Finalizando um programa](../../extensibility/debugger/terminating-a-program.md)

4. [Criando um ponto de interrupção](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Quando um ponto de interrupção liga ou se torna desassociado](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Erros de ponto de interrupção](../../extensibility/debugger/breakpoint-errors.md)

7. [Atingir um ponto de interrupção](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Excluindo um ponto de interrupção](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Entrando no modo de interrupção](../../extensibility/debugger/entering-break-mode.md)

10. [Passando no modo de interrupção](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Avaliação de expressão no modo de interrupção](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Tratamento de exceção](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Confira também
- [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

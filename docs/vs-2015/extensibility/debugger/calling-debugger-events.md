---
title: Chamando eventos do depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f162affe2324afaa8fb1d506c3177311386bfc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146397"
---
# <a name="calling-debugger-events"></a>Chamando eventos do depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eventos em sessões de depuração ocorrem em uma ordem específica.  
  
## <a name="discussion"></a>Discussão  
 Para entender o padrão de chamadas entre o mecanismo de depuração (DE) e o SDM (Gerenciador de depuração de sessão), o seguinte representa a ordem de chamada dos eventos que ocorrem em uma sessão de depuração típica:  
  
1. [Anexando e desanexando a um programa](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2. [Iniciando o depurador](../../extensibility/debugger/launching-the-debugger.md)  
  
3. [Finalizando um programa](../../extensibility/debugger/terminating-a-program.md)  
  
4. [Criando um ponto de interrupção](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5. [Quando um ponto de interrupção liga ou se torna desassociado](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6. [Erros de ponto de interrupção](../../extensibility/debugger/breakpoint-errors.md)  
  
7. [Atingindo um ponto de interrupção](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8. [Excluindo um ponto de interrupção](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Entrando no modo de interrupção](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Passando no modo de interrupção](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Avaliação de expressão no modo de interrupção](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Tratamento de exceção](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

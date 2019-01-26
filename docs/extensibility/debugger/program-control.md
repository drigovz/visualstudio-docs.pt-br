---
title: Controle do programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f6cc27c70076a7c91b6c74e5f1cfed6402555fba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013191"
---
# <a name="program-control"></a>Controle do programa
No Visual Studio de depuração, todos os procedimentos passo a passo e continuando rotinas ocorrerem no nível do programa:  
  
-   Ou seja, definir a próxima instrução, a configuração de seu computador para a próxima instrução a ser executada no ambiente de um determinado quadro  
  
-   Ou seja, executar, continuando sair do modo de depuração  
  
-   Passo a passo para a próxima instrução  
  
-   Continuando com o modo de depuração atual  
  
-   Suspender os threads contidos pelo programa  
  
-   Retomar os threads contidos pelo programa  
  
> [!NOTE]
>  Exibindo a pilha de chamadas é implementada no nível do thread. Para enumerar as informações do quadro ao exibir a pilha de chamadas para um thread, você deve implementar todos os métodos do [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interface.  
  
## <a name="methods-of-program-control"></a>Métodos de controle do programa  
 A tabela a seguir mostra os métodos de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que deve ser implementada para um mecanismo de depuração minimamente funcional (DES) e o controle de execução.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continuar em execução por todos os threads contidos por um programa de um estado parado. Necessário para o controle de execução.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continuar em execução por todos os threads contidos por um programa de um estado parado. Necessário para o controle de execução.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Executa uma etapa em determinado thread. Continua em execução a todos os outros threads contidos pelo programa. Necessário para o controle de execução.|  
  
 Para os programas multithread, você também deve implementar o [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) método e todos os métodos do [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [Avaliação de controle e o estado de execução](../../extensibility/debugger/execution-control-and-state-evaluation.md)
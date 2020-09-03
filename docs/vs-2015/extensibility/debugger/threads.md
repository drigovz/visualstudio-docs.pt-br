---
title: Threads | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 028ad25495ba01d9763c8bec3bbb9c4480d72ff8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185357"
---
# <a name="threads"></a>Threads
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos da arquitetura do depurador, um **thread**:  
  
- É a unidade fundamental de computação. Um thread executa sequencialmente suas instruções no contexto de uma única pilha de chamadas, movendo de um contexto de código para o outro.  
  
- Pode identificar a si mesmo e o programa em que ele está sendo executado, e pode ser nomeado, suspenso e retomado. Um thread também pode enumerar seus quadros de pilhas associados e, em algumas condições, pode ser movido para outro quadro de pilha. Dado o contexto de um quadro de pilha, um thread pode retornar seu thread lógico associado, se houver. Um thread tem propriedades, como uma contagem de suspensão, que pode ser exibida na janela threads do IDE.  
  
- É representado por uma interface [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , normalmente criada por um mecanismo de depuração (de) ou máquina virtual como consequência da execução de um programa.  
  
## <a name="see-also"></a>Consulte Também  
 [Suplementa](../../extensibility/debugger/programs.md)   
 [Quadros de pilha](../../extensibility/debugger/stack-frames.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Gerenciador de sessão de depuração](../../extensibility/debugger/session-debug-manager.md)

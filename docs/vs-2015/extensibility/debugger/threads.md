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
ms.openlocfilehash: c59ef3bdbbd96db82c8e865379907d95227628ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928173"
---
# <a name="threads"></a>Threads
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos de arquitetura do depurador, uma **thread**:  
  
-   É a unidade fundamental de computação. Um thread executa sequencialmente suas instruções dentro do contexto de uma pilha de chamadas, movimentação de contexto de um código para o próximo.  
  
-   Pode identificar em si e o programa que ele está em execução e pode ser chamado, suspenso e retomado. Um thread também pode enumerar seus quadros de pilha associado e, em algumas condições, pode ser movido para outro quadro de pilha. Considerando o contexto de um quadro de pilha, um thread pode retornar seu thread lógico associado, se houver. Um thread tem propriedades, como uma contagem de suspensões, que podem ser exibidos na janela de Threads do IDE.  
  
-   É representado por um [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interface, geralmente criado por um mecanismo de depuração (DES) ou a máquina virtual como consequência de um programa em execução.  
  
## <a name="see-also"></a>Consulte também  
 [Programas](../../extensibility/debugger/programs.md)   
 [Quadros de pilha](../../extensibility/debugger/stack-frames.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Gerenciador de sessão de depuração](../../extensibility/debugger/session-debug-manager.md)

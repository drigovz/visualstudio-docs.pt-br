---
title: Sessão de depuração Manager | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fd7c7555c19f850a15161f6fba00b1184621a9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157833"
---
# <a name="session-debug-manager"></a>Gerenciador de depuração de sessão
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O Gerenciador de sessão de depuração (SDM) gerencia a qualquer número de mecanismos de depuração (DES) qualquer número de programas em vários processos em qualquer número de máquinas de depuração. Além de ser um multiplexador de mecanismo de depuração, o SDM oferece uma exibição unificada da sessão de depuração para o IDE.  
  
## <a name="session-debug-manager-operation"></a>Operação do Gerenciador de depuração de sessão  
 O Gerenciador de sessão de depuração (SDM) gerencia a Alemanha. Pode haver mais de um mecanismo de depuração em execução em um computador ao mesmo tempo. Para multiplexar o DEs, o SDM encapsula um número de interfaces do DEs e as expõe para o IDE como uma única interface.  
  
 Para aumentar o desempenho, algumas interfaces não são multiplexados. Em vez disso, eles são usados diretamente a partir DE, e chamadas para essas interfaces não vão para o SDM. Por exemplo, interfaces usadas com a memória, o código e contextos de documento não são multiplexadas, pois se referem a uma instrução específica, memória ou documento em um determinado programa depurado por um específico DE. Não há outra Alemanha precisa estar envolvido no nível de comunicação.  
  
 Isso não é verdadeiro para todos os contextos. Chamadas para a interface de contexto de avaliação de expressão percorrem o SDM. Durante a avaliação da expressão, o SDM encapsula o [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface que ele oferece ao IDE porque quando essa expressão é avaliada, ela pode envolver vários DEs que está depurando programas no mesmo processo que podem ser em execução no mesmo thread.  
  
 O SDM normalmente funciona como um mecanismo de delegação, mas ele pode atuar como um mecanismo de difusão. Por exemplo, durante a avaliação da expressão, o SDM atua como um mecanismo de difusão para notificar o DEs todos os que eles podem executar código em um thread especificado. Da mesma forma, quando o SDM recebe um evento de interrupção, ele transmite para todos os programas que devem interromper a execução. Quando uma etapa é chamada, o SDM transmite para todos os programas que eles podem continuar em execução. Pontos de interrupção também forem transmitidos para cada DE.  
  
 O SDM não controla o programa atual, thread ou quadro de pilha. O programa, thread e processo informações são enviadas para o SDM em conjunto com eventos de depuração específicos.  
  
## <a name="see-also"></a>Consulte também  
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)   
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)

---
title: Notificando a porta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cf3969dda783882f24d02a748f345cdb66fe413
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838672"
---
# <a name="notifying-the-port"></a>Notificando a porta
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Depois de iniciar um programa, a porta deve ser notificada da seguinte maneira:  
  
1. Quando uma porta recebe um novo nó de programa, ela envia um evento de criação de programa de volta para a sessão de depuração. O evento contém uma interface que representa o programa.  
  
2. A sessão de depuração consulta o programa para o identificador de um mecanismo de depuração (DE) que pode ser anexado.  
  
3. A sessão de depuração verifica se o DE está na lista de DEs permitidos para esse programa. A sessão de depuração obtém essa lista das configurações do programa ativo da solução, originalmente transmitida a ela pelo pacote de depuração.  
  
    O DE deve estar na lista permitida ou, caso contrário, o DE não será anexado ao programa.  
  
   Programaticamente, quando uma porta recebe primeiro um novo nó de programa, ele cria uma interface [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) para representar o programa.  
  
> [!NOTE]
> Isso não deve ser confundido com a `IDebugProgram2` interface criada posteriormente pelo mecanismo de depuração (de).  
  
 A porta envia um evento de criação de programa [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) de volta para o SDM (Gerenciador de depuração de sessão) por meio de uma `IConnectionPoint` interface com.  
  
> [!NOTE]
> Isso não deve ser confundido com a `IDebugProgramCreateEvent2` interface, que é enviada posteriormente pelo de.  
  
 Junto com a própria interface do evento, a porta envia as interfaces [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)e [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , que representam a porta, o processo e o programa, respectivamente. O SDM chama [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) para obter o GUID do que pode depurar o programa. O GUID foi originalmente obtido da interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
 O SDM verifica se o DE está na lista de DEs permitidos. O SDM obtém essa lista das configurações do programa ativo da solução, originalmente transmitida a ela pelo pacote de depuração. O DE deve estar na lista permitida ou, caso contrário, não será anexado ao programa.  
  
 Depois que a identidade de DE for conhecida, o SDM estará pronto para anexá-lo ao programa.  
  
## <a name="see-also"></a>Consulte Também  
 [Iniciando um programa](../../extensibility/debugger/launching-a-program.md)   
 [Anexando após uma inicialização](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)

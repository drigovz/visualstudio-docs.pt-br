---
title: Anexando após uma inicialização | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838739"
---
# <a name="attaching-after-a-launch"></a>Anexando após uma inicialização
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Depois que um programa é iniciado, a sessão de depuração está pronta para anexar o mecanismo DE depuração (DE) ao programa dito.  
  
## <a name="design-decisions"></a>Decisões de design  
 Como a comunicação é mais fácil dentro de um espaço de endereço compartilhado, você deve decidir se faz mais sentido facilitar a comunicação entre a sessão de depuração e a DE, ou entre o e o programa. Escolha entre as seguintes opções:  
  
- Se fizer mais sentido para facilitar a comunicação entre a sessão de depuração e a DE, a sessão de depuração cocriará o DE e solicitará que o DE seja anexado ao programa. Isso deixa a sessão de depuração e outra em um espaço de endereço, e o ambiente e o programa de tempo de execução juntos em outra.  
  
- Se fizer mais sentido para facilitar a comunicação entre o e o programa, o ambiente de tempo de execução cocriará o DE. Isso deixa o SDM em um espaço de endereço e o DE, o ambiente DE tempo DE execução e o programa juntos em outro. Isso é típico de um de que é implementado com um intérprete para executar linguagens com script.  
  
    > [!NOTE]
    > Como o DE anexações ao programa depende da implementação. A comunicação entre o e o programa também depende da implementação.  
  
## <a name="implementation"></a>Implementação  
 Programaticamente, quando o SDM (Gerenciador de depuração de sessão) recebe primeiro o objeto [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que representa o programa a ser iniciado, ele chama o método [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , passando-o para um objeto [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , que posteriormente é usado para passar eventos de depuração de volta para o SDM. `IDebugProgram2::Attach`Em seguida, o método chama o método [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Para obter mais informações sobre como o SDM recebe a `IDebugProgram2` interface, consulte [notificando a porta](../../extensibility/debugger/notifying-the-port.md).  
  
 Se seu DE precisa ser executado no mesmo espaço de endereço que o programa que está sendo depurado, normalmente porque o DE faz parte de um intérprete que executa um script, o `IDebugProgramNodeAttach2::OnAttach` método retorna `S_FALSE` , indicando que ele concluiu o processo de anexo.  
  
 Se, por outro lado, o DE for executado no espaço de endereço do SDM, o `IDebugProgramNodeAttach2::OnAttach` método retornará `S_OK` ou a interface [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) não será implementada no objeto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associado ao programa que está sendo depurado. Nesse caso, o método [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) é eventualmente chamado para concluir a operação de anexação.  
  
 No último caso, você deve chamar o método [Getprogramid](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) no `IDebugProgram2` objeto que foi passado para o `IDebugEngine2::Attach` método, armazenar o `GUID` no objeto de programa local e retornar isso `GUID` quando o `IDebugProgram2::GetProgramId` método for chamado posteriormente neste objeto. O `GUID` é usado para identificar o programa exclusivamente em vários componentes de depuração.  
  
 Observe que, no caso do `IDebugProgramNodeAttach2::OnAttach` método retornando `S_FALSE` , o `GUID` a ser usado para o programa é passado para esse método e é o `IDebugProgramNodeAttach2::OnAttach` método que define o `GUID` no objeto de programa local.  
  
 O DE agora está anexado ao programa e pronto para enviar qualquer evento de inicialização.  
  
## <a name="see-also"></a>Consulte Também  
 [Anexando diretamente a um programa](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notificando a porta](../../extensibility/debugger/notifying-the-port.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Anexa](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Getprogramid](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Desanexar](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)

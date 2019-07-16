---
title: Anexo com base em Iniciar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09a6b39bef9ba6af098bf92d779a490e22492209
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203156"
---
# <a name="launch-based-attachment"></a>Anexo baseado em inicialização
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Com base em inicialização anexo a um programa é automático. Quando o processo que hospeda o programa é iniciado pelo SDM, anexo com base em inicialização segue um caminho semelhante do método manual de anexo. Para obter informações, consulte [anexar ao programa](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>O processo de anexar  
 A principal diferença é a sequência de eventos a seguir a **Attach** chamar, da seguinte maneira:  
  
1. Enviar um **IDebugEngineCreateEvent2** o objeto de evento para o SDM. Para obter detalhes, consulte [enviando eventos](../../extensibility/debugger/sending-events.md).  
  
2. Chame o `IDebugProgram2::GetProgramId` método na **IDebugProgram2** interface é passada para o **Attach** método.  
  
3. Enviar um **IDebugProgramCreateEvent2** objeto de evento para notificar o SDM que local **IDebugProgram2** objeto foi criado para representar o programa para a Alemanha.  
  
4. Enviar um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) o objeto de evento para notificar o SDM que um novo thread é criado para o processo que o iniciou.  
  
## <a name="see-also"></a>Consulte também  
 [Enviar os eventos necessários](../../extensibility/debugger/sending-the-required-events.md)   
 [Habilitar um programa para depuração](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

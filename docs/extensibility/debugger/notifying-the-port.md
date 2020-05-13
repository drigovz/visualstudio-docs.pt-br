---
title: Notificando o Porto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738320"
---
# <a name="notify-the-port"></a>Notifique a porta
Após o lançamento de um programa, a porta deve ser notificada da seguinte forma:

1. Quando uma porta recebe um novo nó de programa, ele envia um evento de criação de programa de volta para a sessão de depuração. O evento traz consigo uma interface que representa o programa.

2. A sessão de depuração consulta o programa para o identificador de um mecanismo de depuração (DE) que pode ser anexado.

3. A sessão de depuração verifica se o DE está na lista de DEs permitidos para esse programa. A sessão de depuração obtém esta lista a partir das configurações ativas do programa da solução, originalmente passadas para ela pelo pacote de depuração.

    O DE deve estar na lista permitida, ou então o DE não será anexado ao programa.

   Programáticamente, quando uma porta recebe pela primeira vez um novo nó de programa, ele cria uma interface [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) para representar o programa.

> [!NOTE]
> Isso não deve ser `IDebugProgram2` confundido com a interface criada posteriormente pelo mecanismo de depuração (DE).

 A porta envia um evento de criação de programa [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) de volta ao `IConnectionPoint` Gerenciador de depuração de sessão (SDM) por meio de uma interface COM.

> [!NOTE]
> Isso não deve ser `IDebugProgramCreateEvent2` confundido com a interface, que é enviada posteriormente pelo DE.

 Junto com a interface de evento em si, a porta envia as interfaces [IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)e [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) que representam a porta, o processo e o programa, respectivamente. O SDM chama [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) para obter o GUID do DE que pode depurar o programa. O GUID foi originalmente obtido a partir da interface [IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

 O SDM verifica se o DE está na lista de DEs permitidos. O SDM obtém esta lista a partir das configurações ativas do programa da solução, originalmente passadas para ela pelo pacote de depuração. O DE deve estar na lista permitida, ou então não será anexado ao programa.

 Uma vez conhecida a identidade do DE, o SDM está pronto para anexá-lo ao programa.

## <a name="see-also"></a>Confira também
- [Lançamento de um programa](../../extensibility/debugger/launching-a-program.md)
- [Anexando após um lançamento](../../extensibility/debugger/attaching-after-a-launch.md)
- [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)

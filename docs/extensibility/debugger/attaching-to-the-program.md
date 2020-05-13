---
title: Anexando ao Programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739245"
---
# <a name="attach-to-the-program"></a>Anexar ao programa
Depois de registrar seus programas com a porta apropriada, você deve anexar o depurador ao programa que deseja depurar.

## <a name="choose-how-to-attach"></a>Escolha como anexar
 Existem três maneiras pelas quais o SDM (Session Debug Manager, gerente de depuração de sessão) tenta anexar ao programa que está sendo depurado.

1. Para programas que são lançados pelo mecanismo de depuração através do método [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (típico de linguagens interpretadas, por exemplo), o SDM obtém a interface [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) do objeto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associado ao programa a ser anexado. Se o SDM `IDebugProgramNodeAttach2` conseguir obter a interface, o SDM então chamará o método [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) O `IDebugProgramNodeAttach2::OnAttach` método `S_OK` retorna para indicar que não se apegou ao programa e que outras tentativas podem ser feitas para anexar ao programa.

2. Se o SDM conseguir obter a interface [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) a partir do programa a que está sendo anexado, o SDM chamará o método [Anexar.](../../extensibility/debugger/reference/idebugprogramex2-attach.md) Essa abordagem é típica para programas que foram lançados remotamente pelo fornecedor portuário.

3. Se o programa não puder `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` ser anexado através dos métodos ou métodos, o SDM `CoCreateInstance` carrega o mecanismo de depuração (se ainda não estiver carregado) ligando para a função e, em seguida, chama o método [Anexar.](../../extensibility/debugger/reference/idebugengine2-attach.md) Essa abordagem é típica para programas lançados localmente por um fornecedor portuário.

    Também é possível que um fornecedor `IDebugEngine2::Attach` portuário personalizado chame o método na `IDebugProgramEx2::Attach` implementação do método pelo fornecedor portuário personalizado. Normalmente, neste caso, o fornecedor de porta personalizado lança o mecanismo de depuração na máquina remota.

   O anexo é alcançado quando o SDM (Session Debug Manager, gerenciador de depuração de sessão) chama o método [Anexar.](../../extensibility/debugger/reference/idebugengine2-attach.md)

   Se você executar seu DE no mesmo processo que o aplicativo a ser depurado, então você deve implementar os seguintes métodos do [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Depois `IDebugEngine2::Attach` que o método for chamado, siga `IDebugEngine2::Attach` estas etapas na implementação do método:

1. Envie um objeto de evento [IDebugCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para o SDM. Para obter mais informações, consulte [Enviar eventos](../../extensibility/debugger/sending-events.md).

2. Ligue para o método [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) no objeto [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que foi passado para o `IDebugEngine2::Attach` método.

     Isso retorna `GUID` um que é usado para identificar o programa. O `GUID` deve ser armazenado no objeto que representa o programa local para o `IDebugProgram2::GetProgramId` DE, e `IDebugProgram2` deve ser devolvido quando o método é chamado na interface.

    > [!NOTE]
    > Se você `IDebugProgramNodeAttach2` implementar a interface, `GUID` o programa `IDebugProgramNodeAttach2::OnAttach` é passado para o método. Isto `GUID` é usado para `GUID` que o `IDebugProgram2::GetProgramId` programa seja devolvido pelo método.

3. Envie um objeto de evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para `IDebugProgram2` notificar o SDM de que o objeto local foi criado para representar o programa ao DE. Para obter detalhes, consulte [Enviar eventos](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Este não é `IDebugProgram2` o mesmo objeto `IDebugEngine2::Attach` que foi passado para o método. O objeto `IDebugProgram2` aprovado anteriormente é reconhecido apenas pela porta e é um objeto separado.

## <a name="see-also"></a>Confira também
- [Anexo baseado em lançamento](../../extensibility/debugger/launch-based-attachment.md)
- [Enviando eventos](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)

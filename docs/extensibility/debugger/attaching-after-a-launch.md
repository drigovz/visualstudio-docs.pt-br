---
title: Anexando após um lançamento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739288"
---
# <a name="attach-after-a-launch"></a>Anexar após um lançamento
Após o lançamento de um programa, a sessão de depuração está pronta para anexar o mecanismo de depuração (DE) ao referido programa.

## <a name="design-decisions"></a>Decisões de design
 Como a comunicação é mais fácil dentro de um espaço de endereço compartilhado, você deve escolher entre duas abordagens de design: definir a comunicação entre a sessão de depuração e o DE. Ou, definir a comunicação entre o DE e o programa. Escolha entre o seguinte:

- Se faz mais sentido configurar a comunicação entre a sessão de depuração e o DE, a sessão de depuração cocria o DE e pede ao DE para anexar ao programa. Este design deixa a sessão de depuração e DE juntos em um espaço de endereço, e o ambiente de tempo de execução e o programa juntos em outro.

- Se faz mais sentido configurar a comunicação entre o DE e o programa, o ambiente de tempo de execução cocria o DE. Este design deixa o SDM em um espaço de endereço e o DE, ambiente de tempo de execução e programajuntos em outro. Este design é típico de um DE que é implementado com um intérprete para executar linguagens roteirizadas.

    > [!NOTE]
    > Como o DE anexa ao programa é dependente da implementação. A comunicação entre o DE e o programa também depende da implementação.

## <a name="implementation"></a>Implementação
 Programáticamente, quando o Gerenciador de depuração de sessão (SDM) recebe pela primeira vez o objeto [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que representa o programa a ser lançado, ele chama o método [Anexar,](../../extensibility/debugger/reference/idebugprogram2-attach.md) passando-o um objeto [IDebugEventCallback2,](../../extensibility/debugger/reference/idebugeventcallback2.md) que mais tarde é usado para transmitir eventos de depuração de volta para o SDM. O `IDebugProgram2::Attach` método então chama o método [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Para obter mais informações sobre como `IDebugProgram2` o SDM recebe a interface, consulte [Notificando a porta](../../extensibility/debugger/notifying-the-port.md).

 Se o seu DE precisar ser executado no mesmo espaço de endereço que o programa que você está depurando: porque o DE é tipicamente parte de um intérprete que está executando um script, o `IDebugProgramNodeAttach2::OnAttach` método retorna `S_FALSE`. O `S_FALSE` retorno indica que ele completou o processo de anexação.

 Se, no entanto, o DE for executado no `IDebugProgramNodeAttach2::OnAttach` espaço `S_OK`de endereço do SDM: o método retorna ou a interface [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) não for implementada no objeto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associado ao programa que você está depurando. Neste caso, o método [Anexar](../../extensibility/debugger/reference/idebugengine2-attach.md) é eventualmente chamado para concluir a operação de anexação.

 Neste último caso, você deve chamar o método `IDebugProgram2` [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) `IDebugEngine2::Attach` no objeto `GUID` que foi passado para o `GUID` método, armazenar o objeto do programa local e devolvê-lo quando o `IDebugProgram2::GetProgramId` método for posteriormente chamado neste objeto. O `GUID` é usado para identificar o programa exclusivamente através dos vários componentes de depuração.

 No caso do `IDebugProgramNodeAttach2::OnAttach` método `S_FALSE`de `GUID` retorno, o uso para o programa é `IDebugProgramNodeAttach2::OnAttach` passado para `GUID` esse método e é o método que define o objeto do programa local.

 O DE está agora anexado ao programa e pronto para enviar quaisquer eventos de inicialização.

## <a name="see-also"></a>Confira também
- [Anexando diretamente a um programa](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Notificando a porta](../../extensibility/debugger/notifying-the-port.md)
- [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)

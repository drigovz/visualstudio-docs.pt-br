---
title: Envio de eventos de startup após um lançamento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713007"
---
# <a name="send-startup-events-after-a-launch"></a>Envie eventos de startup após um lançamento
Uma vez que o motor de depuração (DE) é anexado ao programa, ele envia uma série de eventos de inicialização de volta para a sessão de depuração.

 Os eventos de inicialização enviados de volta para a sessão de depuração incluem:

- Um evento de criação de motores.

- Um evento de criação de programas.

- Criação de threads e eventos de carga de módulos.

- Um evento completo de carga, enviado quando o código está carregado e pronto para ser executado, mas antes que qualquer código seja executado.

  > [!NOTE]
  > Quando este evento é continuado, as variáveis globais são inicializadas e as rotinas de inicialização são executadas.

- Possíveis outros eventos de criação de threads e carga de módulos.

- Um evento de ponto de entrada, que sinaliza que **Main** o `WinMain`programa atingiu seu principal ponto de entrada, como Principal ou . Este evento não é normalmente enviado se o DE se anexar a um programa que já está sendo executado.

  Programáticamente, o DE envia pela primeira vez ao Gerenciador de depuração de sessão (SDM) uma interface [IDebugEngineCreateEvent2,](../../extensibility/debugger/reference/idebugenginecreateevent2.md) que representa um evento de criação de mecanismos, seguido por um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), que representa um evento de criação de programas.

  Esses eventos são normalmente seguidos por um ou mais eventos de criação de thread [iDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) e eventos de carga de módulo [IDebugModuleLoadEvent2.](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)

  Quando o código estiver carregado e pronto para ser executado, mas antes de qualquer código ser executado, o DE envia ao SDM um evento completo de carga [IDebugLoadCompleteEvent2.](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Finalmente, se o programa ainda não estiver sendo executado, o DE envia um evento de ponto de entrada [IDebugEntryPointEvent2,](../../extensibility/debugger/reference/idebugentrypointevent2.md) sinalizando que o programa atingiu seu ponto de entrada principal e está pronto para depuração.

## <a name="see-also"></a>Confira também
- [Controle da execução](../../extensibility/debugger/control-of-execution.md)
- [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)

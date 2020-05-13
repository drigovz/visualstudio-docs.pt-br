---
title: Criando um motor de depuração personalizado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739043"
---
# <a name="create-a-custom-debug-engine"></a>Crie um mecanismo de depuração personalizado
Um mecanismo de depuração (DE) é um componente que permite a depuração de arquiteturas específicas de tempo de execução. Normalmente, há apenas uma implementação DE por ambiente de tempo de execução.

> [!NOTE]
> Embora existam implementações DE separadas para Transact-SQL e JScript, VBScript e JScript compartilham um único DE.

 Um DE trabalha com o intérprete ou sistema de operação para fornecer serviços de depuração como controle de execução, pontos de interrupção e avaliação de expressão. Esses serviços são implementados através das interfaces DE e podem fazer com que o depurador transite entre diferentes modos operacionais. Para obter mais informações, consulte [Modos operacionais](../../extensibility/debugger/operational-modes.md).

 A criação de um DE consiste nas seguintes etapas:

1. Registre um DE com o Visual Studio

2. Permitir que um programa seja depurado

3. Implementar controle de execução e avaliação do estado

4. Enviar eventos

5. Configurar terminação e desapego

## <a name="in-this-section"></a>Nesta seção
 [Registre um mecanismo de depuração personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md) Explica os passos necessários para registrar um motor de depuração com o Visual Studio para que ele possa ser usado.

 [Permitir que um programa seja depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Explica que antes que seu DE possa depurar um programa, você deve primeiro iniciar o DE ou anexá-lo a um programa existente.

 [Implementar controle de execução e avaliação do estado](../../extensibility/debugger/execution-control-and-state-evaluation.md) Discute por que a depuração de um aplicativo requer a implementação de recursos de controle de execução.

 [Enviar eventos](../../extensibility/debugger/sending-events.md) Descreve a comunicação entre o depurador e o DE como um modelo de evento baseado em DCOM.

 [Configurar terminação e desapego](../../extensibility/debugger/termination-and-detaching.md) Explica como alcançar o término normal, o que significa que não há pontos de interrupção, exceções, erros de tempo de execução ou loops infinitos no aplicativo a ser depurado.

 [Eventos de depurador de chamadas](../../extensibility/debugger/calling-debugger-events.md) Documenta a ordem de chamada dos eventos que ocorrem em uma sessão de depuração.

 [Como: Depurar um mecanismo de depuração personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Explica como depurar um DE personalizado.

## <a name="see-also"></a>Confira também
- [Extensibilidade do depurador visual studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

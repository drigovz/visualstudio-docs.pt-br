---
title: Criar um personalizado de mecanismo de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3756eb105ec562d902d4631318e7a5fc698601a2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345311"
---
# <a name="create-a-custom-debug-engine"></a>Criar um mecanismo de depuração personalizado
Um mecanismo de depuração (DES) é um componente que permite a depuração de arquiteturas de tempo de execução específicas. Normalmente, há apenas uma implementação DE cada ambiente de tempo de execução.

> [!NOTE]
> Embora existam implementações DE separadas para Transact-SQL e JScript, VBScript e JScript compartilham um único DE.

 A DE funciona com o sistema de operação ou interpretador para fornecer esses serviços de depuração como avaliação de expressão, os pontos de interrupção e controle de execução. Esses serviços são implementados por meio DE interfaces e podem fazer com que o depurador para fazer a transição entre os modos operacionais diferentes. Para obter mais informações, consulte [modos operacionais](../../extensibility/debugger/operational-modes.md).

 Criando a DE consiste as seguintes etapas:

1. Registrar a DE com o Visual Studio

2. Habilitar um programa a ser depurado

3. Implementar a avaliação de controle e o estado de execução

4. Enviar eventos

5. Configurar o encerramento e desanexação

## <a name="in-this-section"></a>Nesta seção
 [Registrar um mecanismo de depuração personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md) explica as etapas necessárias para registrar um mecanismo de depuração com o Visual Studio para que ele pode ser usado.

 [Habilitar um programa a ser depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) explica que seu Alemanha pode depurar um programa, você deve primeiro iniciar o DE ou anexá-lo a um programa existente.

 [Implementar a avaliação de controle e o estado de execução](../../extensibility/debugger/execution-control-and-state-evaluation.md) aborda por que depurar um aplicativo requer a implementação de recursos de controle de execução.

 [Enviar eventos](../../extensibility/debugger/sending-events.md) descreve a comunicação entre o depurador e DE como um modelo de evento com base no DCOM.

 [Configurar o encerramento e desanexação](../../extensibility/debugger/termination-and-detaching.md) explica como realizar um encerramento normal, o que significa que não há nenhum pontos de interrupção, exceções, erros de tempo de execução ou loops infinitos no aplicativo a ser depurado.

 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md) documenta a ordem de chamada dos eventos que ocorrem em uma sessão de depuração.

 [Como: Depurar um mecanismo de depuração personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) explica como depurar a DE personalizado.

## <a name="see-also"></a>Consulte também
- [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
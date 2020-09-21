---
title: Criando um mecanismo de depuração personalizado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838673"
---
# <a name="creating-a-custom-debug-engine"></a>Criando um mecanismo de depuração personalizado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um mecanismo DE depuração (DE) é um componente que permite a depuração de arquiteturas de tempo de execução específicas. Normalmente, há apenas uma DE implementação por ambiente DE tempo DE execução.  
  
> [!NOTE]
> Embora haja implementações separadas para Transact-SQL e JScript, o VBScript e o JScript compartilham um único DE.  
  
 Um DE funciona com o interpretador ou o sistema operacional para fornecer serviços de depuração como controle de execução, pontos de interrupção e avaliação de expressão. Esses serviços são implementados por meio de interfaces e podem fazer com que o depurador faça a transição entre diferentes modos operacionais. Para obter mais informações, consulte [modos operacionais](../../extensibility/debugger/operational-modes.md).  
  
 A criação de um de consiste nas seguintes etapas:  
  
1. Registrando um DE com o Visual Studio  
  
2. Habilitando um programa a ser depurado  
  
3. Controle de execução e avaliação de estado  
  
4. Enviando eventos  
  
5. Encerramento e desanexação  
  
## <a name="in-this-section"></a>Nesta seção  
 [Registrando um mecanismo de depuração personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explica as etapas necessárias para registrar um mecanismo de depuração com o Visual Studio para que ele possa ser usado.  
  
 [Habilitando um programa a ser depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Explica que, antes que o DE possa depurar um programa, você deve primeiro iniciar o ou anexá-lo a um programa existente.  
  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Discute por que depurar um aplicativo requer a implementação de recursos de controle de execução.  
  
 [Enviando eventos](../../extensibility/debugger/sending-events.md)  
 Descreve a comunicação entre o depurador e o DE como um modelo DE evento baseado no DCOM.  
  
 [Término e desconexão](../../extensibility/debugger/termination-and-detaching.md)  
 Explica como obter um encerramento normal, o que significa que não há pontos de interrupção, exceções, erros de tempo de execução ou loops infinitos no aplicativo a ser depurado.  
  
 [Chamando eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)  
 Documenta a ordem de chamada dos eventos que ocorrem em uma sessão de depuração.  
  
 [Como depurar um mecanismo de depuração personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explica como depurar um DE.  
  
## <a name="see-also"></a>Consulte Também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

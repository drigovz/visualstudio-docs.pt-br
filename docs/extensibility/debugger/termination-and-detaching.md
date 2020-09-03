---
title: Encerramento e desanexação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712490"
---
# <a name="termination-and-detaching"></a>Encerramento e desanexação
A seção a seguir descreve o encerramento normal.

## <a name="discussion"></a>Discussão
 Depois que a interface [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) continuar, se não houver nenhum ponto de interrupção, exceções, erros em tempo de execução ou loops infinitos no aplicativo a ser depurado, o programa que está sendo depurado será executado até a conclusão. Esse processo é um encerramento normal.

 Você deve enviar um [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) para implementar o encerramento normal. A finalização normal requer a execução do método [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Confira também
- [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

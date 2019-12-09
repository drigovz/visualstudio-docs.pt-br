---
title: Encerramento e desanexação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8aafb94e0a07462d93cc77a34f7199f61f944d0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333719"
---
# <a name="termination-and-detaching"></a>Encerramento e desanexação
A seção a seguir descreve um encerramento normal.

## <a name="discussion"></a>Discussão
 Após o [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interface continua, se não houver nenhum pontos de interrupção, exceções, erros de tempo de execução ou loops infinitos no aplicativo a ser depurado, o programa que está sendo depurado seja concluída. Esse processo é um encerramento normal.

 Você deve enviar uma [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) para implementar um encerramento normal. Um encerramento normal exigirá a execução de [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) método.

## <a name="see-also"></a>Consulte também
- [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
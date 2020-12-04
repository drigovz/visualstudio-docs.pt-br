---
title: Método NotifyDebuggerOfWaitCompletion | Microsoft Docs
description: Saiba mais sobre o método NotifyDebuggerOfWaitCompletion, que é um espaço reservado usado como um destino de ponto de interrupção pelo depurador.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35571b28287ecdea48a2ff089cb25cf3ed742d60
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606626"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Método NotifyDebuggerOfWaitCompletion
Método de espaço reservado usado como um destino de ponto de interrupção pelo depurador. Este método não deve ser embutido nem ser otimizado.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (no *mscorlib.dll*)

## <a name="syntax"></a>Sintaxe

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Comentários
 Todas as operações de junção com uma tarefa devem chamar esse método se o bit de notificação do depurador for definido.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Confira também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)

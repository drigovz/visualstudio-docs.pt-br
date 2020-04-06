---
title: NotificarDebuggerOfWaitMétodo de conclusão | Microsoft Docs
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
ms.openlocfilehash: 8963e29a067754c0e8c89b9db336b239ac682ce1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738339"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotificarDebuggerDeOmétodoDeConclusão
Método de espaço reservado usado como alvo de ponto de ruptura pelo depurador. Este método não deve ser inforrado ou otimizado.

 **Espaço de nome:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montagem:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Sintaxe

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Comentários
 Todas as operações com uma tarefa devem chamar esse método se a bit de notificação do depurador estiver definida.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Confira também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)

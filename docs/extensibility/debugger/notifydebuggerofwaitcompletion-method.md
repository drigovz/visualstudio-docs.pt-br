---
title: Método NotifyDebuggerOfWaitCompletion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28811ba402803d1ddb9a6dd08a18d32db6257386
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889407"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Método NotifyDebuggerOfWaitCompletion
Método de espaço reservado usado como um destino de ponto de interrupção pelo depurador. Esse método não deve ser embutida ou otimizado.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (em *mscorlib. dll*)

## <a name="syntax"></a>Sintaxe

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Comentários
 Todas as operações de junção com uma tarefa devem chamar esse método se suas bit de notificação do depurador está definido.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Consulte também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)
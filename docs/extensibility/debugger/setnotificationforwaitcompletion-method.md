---
title: Método de conclusão do SetNotificationWaitWait | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712868"
---
# <a name="setnotificationforwaitcompletion-method"></a>Método SetNotificationForWaitCompletion
Define ou limpa a TASK_STATE_WAIT_COMPLETION_NOTIFICATION parte do estado.

 **Espaço de nome:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montagem:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Sintaxe

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>parâmetros
 `enabled`

 `true`para definir a broca; `false` para desdefinir a broca.

## <a name="exceptions"></a>Exceções

## <a name="remarks"></a>Comentários
 O depurador define esta broca para ajudar a sair de um corpo de método assíncrono. Se `enabled` `true`for, este método deve ser chamado apenas em uma tarefa que ainda não foi concluída. Quando `enabled` `false`é , este método pode ser chamado em tarefas concluídas. Em ambos os casoes, ele só deve ser usado para tarefas de estilo de promessa.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Confira também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)

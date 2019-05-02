---
title: Método SetNotificationForWaitCompletion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 468850a441cfd0bc87155fd746d8578c6b763e66
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912920"
---
# <a name="setnotificationforwaitcompletion-method"></a>Método SetNotificationForWaitCompletion
Define ou limpa o bit de estado TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (em *mscorlib. dll*)

## <a name="syntax"></a>Sintaxe

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parâmetros
 `enabled`

 `true` Para definir o bit; `false` para remover o bit.

## <a name="exceptions"></a>Exceções

## <a name="remarks"></a>Comentários
 O depurador definirá esse bit para ajudá-lo fora de um corpo de método assíncrono. Se `enabled` é `true`, esse método deve ser chamado somente em uma tarefa que ainda não foi concluída. Quando `enabled` é `false`, esse método pode ser chamado em tarefas concluídas. Em ambos os casos, ele só deve ser usado para tarefas de estilo de promessa.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Consulte também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)
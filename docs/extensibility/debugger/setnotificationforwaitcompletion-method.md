---
title: Método SetNotificationForWaitCompletion | Microsoft Docs
description: Saiba como o depurador usa um bit de estado para ajudar a sair de um corpo de método assíncrono para tarefas de estilo Promise.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 80904e95c1561dd20ed2a6cc9ad561e6c18ee93a
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845213"
---
# <a name="setnotificationforwaitcompletion-method"></a>Método SetNotificationForWaitCompletion
Define ou limpa o bit de estado TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (no *mscorlib.dll*)

## <a name="syntax"></a>Sintaxe

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parâmetros
 `enabled`

 `true` para definir o bit; `false` para remover a definição do bit.

## <a name="exceptions"></a>Exceções

## <a name="remarks"></a>Comentários
 O depurador define esse bit para ajudar a depurar um corpo de método assíncrono. Se `enabled` for `true` , esse método deve ser chamado apenas em uma tarefa que ainda não foi concluída. Quando `enabled` é `false` , esse método pode ser chamado em tarefas concluídas. Em ambos os eventos, ele só deve ser usado para tarefas de estilo Promise.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Confira também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)

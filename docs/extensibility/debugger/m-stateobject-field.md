---
title: Campo de m_stateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bbf16af65ab59147614ce5609de9b56ff833862a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925124"
---
# <a name="m_stateobject-field"></a>campo de m_stateObject
Um objeto que representa os dados que serão usados pela ação.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (no *mscorlib.dll*)

 Como você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Comentários
 Esse é o `state` parâmetro no <xref:System.Threading.Tasks.Task.%23ctor%2A> Construtor. Também é o campo de apoio para a <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propriedade.

## <a name="see-also"></a>Confira também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)

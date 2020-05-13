---
title: campo m_action | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 925141733356ac7730e2708673ebdad793fd465b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738440"
---
# <a name="m_action-field"></a>m_action campo
O delegado que representa o código <xref:System.Threading.Tasks.Task> para executar no objeto.

 **Espaço de nome:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montagem:** mscorlib (in *mscorlib.dll*)

 Como você não pode acessar este membro interno do .NET Framework, a seguinte sintaxe é fornecida na Linguagem Intermediária Comum (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Comentários
 Este é `action` o parâmetro <xref:System.Threading.Tasks.Task.%23ctor%2A> na construtora.

## <a name="see-also"></a>Confira também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)

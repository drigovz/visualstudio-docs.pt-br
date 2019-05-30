---
title: m_stateObject Field | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95947a1367ea1ddf4aa88689f731971d5c7d0a6c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330840"
---
# <a name="mstateobject-field"></a>m_stateObject field
Um objeto que representa os dados que usará a ação.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (em *mscorlib. dll*)

 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Comentários
 Esse é o `state` parâmetro no <xref:System.Threading.Tasks.Task.%23ctor%2A> construtor. Também é o campo de suporte para o <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propriedade.

## <a name="see-also"></a>Consulte também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)
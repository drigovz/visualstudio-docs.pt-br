---
title: campo m_stateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fed70f2eda19ad96454a83217c20c046809f3034
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738379"
---
# <a name="m_stateobject-field"></a>m_stateObject campo
Um objeto que representa dados que a ação usará.

 **Espaço de nome:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montagem:** mscorlib (in *mscorlib.dll*)

 Como você não pode acessar este membro interno do .NET Framework, a seguinte sintaxe é fornecida na Linguagem Intermediária Comum (CIL).

## <a name="syntax"></a>Sintaxe

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Comentários
 Este é `state` o parâmetro <xref:System.Threading.Tasks.Task.%23ctor%2A> na construtora. É também o campo <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> de apoio para a propriedade.

## <a name="see-also"></a>Confira também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)

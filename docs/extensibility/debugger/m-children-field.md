---
title: m_children Field | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab6446b18350fe1f11e0b164d9eb4bff39035ddb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330886"
---
# <a name="mchildren-field"></a>m_children field
A lista de tarefas filho que estão registrados com essa tarefa.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (em *mscorlib. dll*)

 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Comentários
 Enquanto a tarefa está em execução, somente o thread que executa a tarefa deve acessar essa matriz.

 Se a tarefa for concluída, outros threads podem acessar este campo desde que eles não adiciona nada a ele ou remover nada dela.

## <a name="see-also"></a>Consulte também
- [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
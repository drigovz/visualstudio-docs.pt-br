---
title: Campo m_action | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b41c5d0ae7733a2a9256882852b9016d8e05e0bc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944451"
---
# <a name="maction-field"></a>campo m_action
O delegado que representa o código seja executado no <xref:System.Threading.Tasks.Task> objeto.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em *mscorlib. dll*)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp  
.field assembly object m_action  
```  
  
## <a name="remarks"></a>Comentários  
 Esse é o `action` parâmetro no <xref:System.Threading.Tasks.Task.%23ctor%2A> construtor.  
  
## <a name="see-also"></a>Consulte também  
 [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)
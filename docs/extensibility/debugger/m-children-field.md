---
title: Campo m_children | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5d924e0439be2f8ab615d18a61f1303994b8dde
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923686"
---
# <a name="mchildren-field"></a>campo m_children
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
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
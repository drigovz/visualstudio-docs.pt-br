---
title: Campo de m_action | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1506827a1132c659b1082d0f3d4aed9a21b417d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149105"
---
# <a name="m_action-field"></a>Campo m_action
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O delegado que representa o código a ser executado no <xref:System.Threading.Tasks.Task> objeto.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (no mscorlib.dll)  
  
 Como você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field assembly object m_action  
```  
  
## <a name="remarks"></a>Comentários  
 Esse é o `action` parâmetro no <xref:System.Threading.Tasks.Task.%23ctor%2A> Construtor.  
  
## <a name="see-also"></a>Consulte Também  
 [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)

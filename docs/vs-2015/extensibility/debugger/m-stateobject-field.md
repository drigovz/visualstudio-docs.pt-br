---
title: Campo de m_stateObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e9cfc6f689504bef2a8366f90282641d1e9e105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149048"
---
# <a name="m_stateobject-field"></a>Campo m_stateObject
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um objeto que representa os dados que serão usados pela ação.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (no mscorlib.dll)  
  
 Como você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Comentários  
 Esse é o `state` parâmetro no <xref:System.Threading.Tasks.Task.%23ctor%2A> Construtor. Também é o campo de apoio para a <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propriedade.  
  
## <a name="see-also"></a>Consulte Também  
 [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)

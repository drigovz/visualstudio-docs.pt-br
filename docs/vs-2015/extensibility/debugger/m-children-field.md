---
title: Campo m_children | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 749b7a8da2cbdf8377e7f2e1fcb39787e2f42303
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149057"
---
# <a name="mchildren-field"></a>Campo m_children
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A lista de tarefas filho que estão registrados com essa tarefa.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Comentários  
 Enquanto a tarefa está em execução, somente o thread que executa a tarefa deve acessar essa matriz.  
  
 Se a tarefa for concluída, outros threads podem acessar este campo desde que eles não adiciona nada a ele ou remover nada dela.  
  
## <a name="see-also"></a>Consulte também  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)

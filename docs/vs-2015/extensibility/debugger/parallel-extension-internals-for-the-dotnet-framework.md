---
title: Elementos internos de extensões em paralelo para o .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a7a0cc60f9398e073bcce59f6e03d62d3bb0820
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929205"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Internos de extensão paralela para o .NET Framework
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta seção descreve os tipos internos, métodos, e campos de classes que ajudam você a implementam um depurador personalizado para as extensões paralelas para o .NET Framework.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)  
 Descreve os membros de dados interno a <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe.  
  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Descreve os membros de dados interno a <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe.  
  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Descreve os membros de dados interno a `System.Threading.Tasks.ContingentProperties` classe.  
  
 [Estrutura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Descreve os membros internos do <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> estrutura.  
  
 [Estrutura AsyncTaskMethodBuilder\<TResult >](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Descreve os membros internos do <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> estrutura.  
  
 [Estrutura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Descreve os membros internos do <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> estrutura.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Programação paralela](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)

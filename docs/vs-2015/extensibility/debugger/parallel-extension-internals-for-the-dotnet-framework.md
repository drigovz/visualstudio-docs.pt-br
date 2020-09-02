---
title: Elementos internos de extensão paralela para o .NET Framework | Microsoft Docs
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
ms.openlocfilehash: 42c472190469e7d008fa8c525f50eabfaf37053f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65680934"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Internos de extensão paralela para o .NET Framework
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta seção descreve os tipos internos, os métodos e os campos de classes que ajudam a implementar um depurador personalizado para as extensões paralelas para o .NET Framework.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)  
 Descreve os membros de dados internos da <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe.  
  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Descreve os membros de dados internos da <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe.  
  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Descreve os membros de dados internos da `System.Threading.Tasks.ContingentProperties` classe.  
  
 [Estrutura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Descreve os membros internos da <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> estrutura.  
  
 [Estrutura AsyncTaskMethodBuilder\<TResult>](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Descreve os membros internos da <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> estrutura.  
  
 [Estrutura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Descreve os membros internos da <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> estrutura.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Programação paralela](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)

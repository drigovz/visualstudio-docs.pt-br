---
title: Elementos internos de extensão paralela para o .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3583e94a0bfff4474db03aa9d083add921f3da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738264"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Elementos internos de extensão paralela para o .NET Framework
Esta seção descreve os tipos internos, os métodos e os campos de classes que ajudam a implementar um depurador personalizado para as extensões paralelas para o .NET Framework.

## <a name="in-this-section"></a>Nesta seção
 [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md) Descreve os membros de dados internos da <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe.

 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) Descreve os membros de dados internos da <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe.

 [Classe contingentproperties](../../extensibility/debugger/contingentproperties-class-internal-members.md) Descreve os membros de dados internos da `System.Threading.Tasks.ContingentProperties` classe.

 [Estrutura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Descreve os membros internos da <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> estrutura.

 [A \<TResult> estrutura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) descreve os membros internos da <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> estrutura.

 [Estrutura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Descreve os membros internos da <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> estrutura.

## <a name="see-also"></a>Confira também
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programação paralela](/dotnet/standard/parallel-programming/index)

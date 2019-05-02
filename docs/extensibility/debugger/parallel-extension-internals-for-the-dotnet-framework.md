---
title: Elementos internos de extensões em paralelo para o .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0437363dd7d45b95a04a9e58edd45229f14b4c93
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925356"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Elementos internos de extensões paralelas para o .NET Framework
Esta seção descreve os tipos internos, métodos, e campos de classes que ajudam você a implementam um depurador personalizado para as extensões paralelas para o .NET Framework.

## <a name="in-this-section"></a>Nesta seção
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md) descreve os membros de dados interno a <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe.

 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) descreve os membros de dados interno a <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe.

 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md) descreve os membros de dados interno a `System.Threading.Tasks.ContingentProperties` classe.

 [Estrutura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) descreve os membros internos do <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> estrutura.

 [AsyncTaskMethodBuilder\<TResult > estrutura](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) descreve os membros internos do <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> estrutura.

 [Estrutura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) descreve os membros internos do <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> estrutura.

## <a name="see-also"></a>Consulte também
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programação paralela](/dotnet/standard/parallel-programming/index)
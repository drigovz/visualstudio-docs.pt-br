---
title: Internals de extensão paralela para o Quadro .NET | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738264"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Internos de extensão paralelas para o Quadro .NET
Esta seção descreve os tipos internos, métodos e campos de classes que ajudam você a implementar um depurador personalizado para as extensões paralelas ao .NET Framework.

## <a name="in-this-section"></a>Nesta seção
 [Classe de tarefas](../../extensibility/debugger/task-class-internal-members.md) Descreve os dados internos <xref:System.Threading.Tasks.Task?displayProperty=fullName> membros da classe.

 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) Descreve os dados internos <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> membros da classe.

 [Classe Propriedades Contingentes](../../extensibility/debugger/contingentproperties-class-internal-members.md) Descreve os dados internos `System.Threading.Tasks.ContingentProperties` membros da classe.

 [Estrutura do AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Descreve os membros internos <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> da estrutura.

 [AsyncTaskMethodBuilder\<TResult> estrutura](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) Descreve os <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> membros internos da estrutura.

 [Estrutura do AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Descreve os membros internos <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> da estrutura.

## <a name="see-also"></a>Confira também
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Extensibilidade do depurador visual studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programação paralela](/dotnet/standard/parallel-programming/index)

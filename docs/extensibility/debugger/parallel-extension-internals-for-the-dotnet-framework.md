---
title: Elementos internos de extensão paralela para o .NET Framework | Microsoft Docs
description: Esses recursos descrevem tipos, métodos e campos internos de classes usados para implementar um depurador personalizado para as extensões paralelas para o .NET Framework.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f9625af464e2695c6dd4302f4f7590d20e8f6af7
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606587"
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

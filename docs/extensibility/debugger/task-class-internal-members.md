---
title: Classe Tarefa - Membros Internos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712741"
---
# <a name="task-class---internal-members"></a>Classe de tarefas - membros internos
Este artigo descreve os membros <xref:System.Threading.Tasks.Task?displayProperty=fullName> internos da classe que ajudam você a implementar um depurador personalizado. Para obter informações gerais sobre <xref:System.Threading.Tasks.Task> esta classe, consulte o artigo de referência.

 **Espaço de nome:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montagem:** mscorlib (in *mscorlib.dll*)

 Como você não pode acessar esses membros internos do Quadro .NET, a seguinte sintaxe é fornecida na Linguagem Intermediária Comum (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>Membros

### <a name="methods"></a>Métodos

|Nome|Descrição|
|----------|-----------------|
|[Método SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Define ou limpa a TASK_STATE_WAIT_COMPLETION_NOTIFICATION parte do estado.|
|[Método NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Método de espaço reservado usado como alvo de ponto de ruptura pelo depurador.|

### <a name="fields"></a>Campos

|Nome|Descrição|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|O delegado que representa o código <xref:System.Threading.Tasks.Task> para executar no objeto.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Armazena propriedades adicionais do <xref:System.Threading.Tasks.Task> objeto.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|O campo de <xref:System.Threading.Tasks.Task?displayProperty=fullName> apoio para a propriedade dos pais.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Armazena informações sobre o <xref:System.Threading.Tasks.Task> estado atual do objeto.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Um objeto que representa dados que serão usados pela ação.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|O campo de <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> apoio para a propriedade.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|O próximo identificador <xref:System.Threading.Tasks.Task> disponível para um objeto.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica que a tarefa foi cancelada antes de chegar ao estado em execução, ou que a tarefa confirmou seu cancelamento e foi concluída sem exceção.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica que a tarefa está em execução.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica que a tarefa foi concluída por causa de uma exceção não tratada.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica que a tarefa completou a execução com sucesso.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica que a tarefa terminou de executar seu delegado e está implicitamente esperando que tarefas de criança anexadas sejam concluídas.|

## <a name="remarks"></a>Comentários
 Os seguintes métodos internos são úteis para um <xref:System.Threading.Tasks.Task> mecanismo de depurador porque marcam a entrada para a execução do código:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Confira também
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Internos de extensão paralelas para o Quadro .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

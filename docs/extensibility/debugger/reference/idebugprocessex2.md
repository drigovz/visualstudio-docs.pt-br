---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723332"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Essa interface permite que o SDM (Gerenciador de depuração de sessão) Notifique um processo que está sendo anexado ou desanexado do processo.

## <a name="syntax"></a>Syntax

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um fornecedor de porta personalizado implementa essa interface no mesmo objeto que a interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) para:

- Controle de suporte de sessões conectadas a um processo

- Suporte à anexação automática em vários mecanismos de depuração

  O fornecedor da porta personalizada pode implementar essa interface se escolher.

## <a name="notes-for-callers"></a>Observações para chamadores

- O SDM chama [QueryInterface](/cpp/atl/queryinterface) em uma `IDebugProcess2` interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A tabela a seguir mostra os métodos de `IDebugProcessEx2` .

|Método|Descrição|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa ao processo que uma sessão está depurando o processo agora.|
|[Desanexar](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa ao processo que uma sessão não está mais Depurando o processo.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Adiciona nós de programa para uma lista de mecanismos de depuração.|

## <a name="remarks"></a>Comentários
 Essa interface é privada entre o SDM e o processo.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Portpriv. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

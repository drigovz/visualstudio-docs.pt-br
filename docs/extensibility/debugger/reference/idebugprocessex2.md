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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723332"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Essa interface permite que o SDM (Session Debug Manager, gerenciador de depuração de sessão) notifique um processo ao que está anexando ou se desvinculando do processo.

## <a name="syntax"></a>Sintaxe

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um fornecedor de porta personalizado implementa essa interface no mesmo objeto que a interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) para:

- Suporte ao rastreamento de sessões conectadas a um processo

- Suporte a conexão automática em vários mecanismos de depuração

  O fornecedor de porta personalizado pode implementar esta interface se quiser.

## <a name="notes-for-callers"></a>Observações para chamadores

- O SDM chama [queryInterface](/cpp/atl/queryinterface) em uma `IDebugProcess2` interface para obter esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugProcessEx2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa o processo que uma sessão está depurando o processo.|
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa o processo que uma sessão não está mais depurando o processo.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Adiciona nós de programa para uma lista de motores de depuração.|

## <a name="remarks"></a>Comentários
 Esta interface é privada entre o SDM e o processo.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

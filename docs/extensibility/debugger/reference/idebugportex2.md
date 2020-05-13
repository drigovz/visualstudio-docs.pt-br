---
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5789681b0da70f46dadac1e29d0d6bb9dc905d1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725003"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Essa interface permite que o SDM (Session Debug Manager, gerenciador de depuração de sessão) controle os programas e processos em execução em uma porta.

## <a name="syntax"></a>Sintaxe

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um fornecedor de porta personalizado implementa essa interface no mesmo objeto que implementa [o IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Observações para chamadores
 O SDM chama [queryInterface](/cpp/atl/queryinterface) na `IDebugPort2` interface para obter esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugPortEx2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Lança um arquivo executável.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Retoma a execução de um processo.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina se um processo pode ser encerrado.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Termina um processo.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Obtém a id de processo da própria porta.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Tem um programa associado a um nó de programa.|

## <a name="remarks"></a>Comentários
 Esta interface é normalmente privada entre o SDM e o fornecedor de porta personalizado.

 Se desejar, um mecanismo de depuração (DE) pode procurar por esta interface na interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) passada para [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) e usar [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) para iniciar o programa. Isso não é um requisito, no entanto, e um DE pode fazer o que for necessário para lançar o programa de solicitação.

## <a name="requirements"></a>Requisitos
 Cabeçalho: portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735397"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Esta interface informa ao Gerenciador de Depuração de Sessão (SDM) que uma quebra assíncrona foi concluída com sucesso.

## <a name="syntax"></a>Sintaxe

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O DE implementa essa interface para suportar pausas de usuário em um programa. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que esta interface (o SDM usa [queryInterface](/cpp/atl/queryinterface) para acessar a `IDebugEvent2` interface).

## <a name="notes-for-callers"></a>Observações para chamadores
 O SDM chama [causebreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) quando o usuário solicitou que o programa que está sendo depurado seja pausado. Quando o programa foi pausado com `IDebugBreakEvent2` sucesso, o DE envia o evento. Este evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornecida pelo SDM quando anexada ao programa que está sendo depurado.

## <a name="remarks"></a>Comentários
 Por exemplo, um usuário pode selecionar o comando **Break All** no menu **Debug** para sair de um programa que está executando um loop infinito. O SDM diz ao programa para parar chamando [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). O DE `IDebugBreakEvent2` envia quando o programa finalmente pára.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

---
title: IDebugProgram2::Continue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ca9d7841671c44702b883cc8efcc23e803ea8fe
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693679"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continua a execução deste programa de um estado parado. Qualquer estado de execução anterior (por exemplo, uma etapa) é preservado, e o programa inicia a execução novamente.

> [!NOTE]
>  Este método foi preterido. Use o [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) método em vez disso.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

#### <a name="parameters"></a>Parâmetros
 `pThread`

 [in] Uma [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método é chamado neste programa, independentemente de quantos aplicativos estão sendo depurados, ou qual programa gerou o evento de interrupção. A implementação deve manter o estado de execução anterior (por exemplo, uma etapa) e continuar a execução como se ele nunca foi interrompido antes de concluir sua execução anterior. Ou seja, se um thread nesse programa estava fazendo uma operação de percorrer e foi interrompido porque algum outro programa é interrompido e, em seguida, esse método foi chamado, o programa deve concluir a operação percorrer original.

> [!WARNING]
>  Não enviar um evento de interrupção ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao manipular essa chamada; caso contrário, o depurador poderá parar de responder.

## <a name="see-also"></a>Consulte também
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
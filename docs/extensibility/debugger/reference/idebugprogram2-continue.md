---
title: IDebugProgram2::Continuar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d04445a7a1c444f30a0ef5c156dcd7ad744c6f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723070"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continua executando este programa de um estado parado. Qualquer estado de execução anterior (como um passo) é preservado, e o programa começa a ser executado novamente.

> [!NOTE]
> Esse método é preterido. Use o método [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) em vez disso.

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

## <a name="parameters"></a>parâmetros
`pThread`[em] Um objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o segmento.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método é chamado neste programa, independentemente de quantos programas estão sendo depurados, ou qual programa gerou o evento de parada. A implementação deve manter o estado de execução anterior (como um passo) e continuar a execução como se nunca tivesse parado antes de completar sua execução anterior. Ou seja, se um segmento neste programa estava fazendo uma operação de step-over e foi interrompido porque algum outro programa parou, e então esse método foi chamado, o programa deve completar a operação de step-over original.

> [!WARNING]
> Não envie um evento de parada ou um evento imediato (síncrono) para [o Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante o tratamento desta chamada; caso contrário, o depurador pode travar.

## <a name="see-also"></a>Confira também
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

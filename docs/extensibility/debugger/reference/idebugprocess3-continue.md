---
title: IDebugProcess3::Continue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723772"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continua executando este processo a partir de um estado parado. Qualquer estado de execução anterior (como uma etapa) é preservado, e o processo começa a ser executado novamente.

> [!NOTE]
> Este método deve ser usado em vez de [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
`pThread`\
[em] Um objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) representando o segmento a ser continuado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro.

## <a name="remarks"></a>Comentários
 Esse método é chamado neste processo, independentemente de quantos processos estão sendo depurados ou qual processo gerou o evento de parada. A implementação deve manter o estado de execução anterior (como um passo) e continuar a execução como se nunca tivesse parado antes de completar sua execução anterior. Ou seja, se um segmento nesse processo estava fazendo uma operação de step-over e foi interrompido porque algum outro processo parou, e depois `Continue` foi chamado, o segmento especificado deve concluir a operação de over-over original.

 **Aviso** Não envie um evento de parada ou um evento imediato (síncrono) para [o Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante o tratamento desta chamada; caso contrário, o depurador pode travar.

## <a name="see-also"></a>Confira também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

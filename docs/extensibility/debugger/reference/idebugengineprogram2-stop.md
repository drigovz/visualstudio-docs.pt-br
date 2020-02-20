---
title: 'IDebugEngineProgram2:: Stop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d7213dcd2484ba69caf51fdc21f52bba5bb3361
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506452"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Interrompe todos os threads em execução neste programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é chamado quando este programa está sendo depurado em um ambiente com vários programas. Quando um evento de parada de algum outro programa é recebido, esse método é chamado neste programa. A implementação desse método deve ser assíncrona; ou seja, nem todos os threads devem ser interrompidos antes que esse método seja retornado. A implementação desse método pode ser tão simples quanto chamar o método [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) neste programa.

 Os implementadores devem enviar um [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) quando o programa parar.

## <a name="see-also"></a>Confira também
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)

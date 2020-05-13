---
title: IDebugEngineProgram2::Stop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 286a448ee33f57d2e3a3282dc8d72b11a843a9c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730487"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Interrompe todos os segmentos que estão sendo executados neste programa.

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
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método é chamado quando este programa está sendo depurado em um ambiente multiprograma. Quando um evento de parada de algum outro programa é recebido, este método é chamado neste programa. A implementação deste método deve ser assíncrona; ou seja, nem todos os segmentos devem ser necessários para serem interrompidos antes que este método retorne. A implementação deste método pode ser tão simples quanto chamar o método [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) neste programa.

 Os implementadores devem enviar um [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) quando o programa parar.

## <a name="see-also"></a>Confira também
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)

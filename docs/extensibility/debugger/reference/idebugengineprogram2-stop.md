---
title: IDebugEngineProgram2::Stop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3cb9627ba11bdec5729383bd6a31e4a338f3ef9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920339"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Interrompe todos os threads em execução nesse programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é chamado quando este programa está sendo depurado em um ambiente de vários programa. Quando um evento de interrupção de algum outro programa for recebido, este método é chamado neste programa. A implementação deste método deve ser assíncrona; ou seja, nem todos os threads devem ser necessárias para ser interrompido antes desse método retorna. A implementação desse método pode ser tão simple quanto chamar o [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) método neste programa.

 Nenhum evento de depuração é enviado em resposta a esse método.

## <a name="see-also"></a>Consulte também
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
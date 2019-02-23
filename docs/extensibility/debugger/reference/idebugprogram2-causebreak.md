---
title: IDebugProgram2::CauseBreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06b392dd10c364e746f592a4d0ffd9ac32ca7df9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720193"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Solicitações que o programa parar a execução a próxima hora em que uma das suas tentativas de threads para executar.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Uma [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) evento é enviado quando o programa tenta executar código após esse método é chamado em seguida.

 Esse método é assíncrono, em que o método retornará imediatamente sem esperar que o programa pare necessariamente.

## <a name="see-also"></a>Consulte também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
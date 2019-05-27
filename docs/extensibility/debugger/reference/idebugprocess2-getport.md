---
title: IDebugProcess2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetPort
helpviewer_keywords:
- IDebugProcess2::GetPort
ms.assetid: e39b6e5a-64eb-48cf-a53d-da4fdb968e2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7885f43d10f2644071e993697b04024fea2bc40
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202590"
---
# <a name="idebugprocess2getport"></a>IDebugProcess2::GetPort
Obtém a porta que o processo está sendo executado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPort( 
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Parâmetros
`ppPort`\
[out] Retorna um [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa a porta na qual o processo foi iniciado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
---
title: IEnumDebugThreads2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Reset
helpviewer_keywords:
- IEnumDebugThreads2::Reset
ms.assetid: 88980d9a-c4d6-4de4-a9ab-fb56fa71394a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0eef830808f413fe6a52239ddf50625dcaabc29
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461151"
---
# <a name="ienumdebugthreads2reset"></a>IEnumDebugThreads2::Reset
Redefine a enumeração para o primeiro elemento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Depois que esse método é chamado, a próxima chamada para o [próxima](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md) método retorna o primeiro elemento da enumeração.

## <a name="see-also"></a>Consulte também
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
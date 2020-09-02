---
title: 'IEnumDebugThreads2:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Reset
helpviewer_keywords:
- IEnumDebugThreads2::Reset
ms.assetid: 88980d9a-c4d6-4de4-a9ab-fb56fa71394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f90a0d130d69a0c710c89bb346ad9756ac54289
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715117"
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

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Depois que esse método é chamado, a próxima chamada para o [próximo](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md) método retorna o primeiro elemento da enumeração.

## <a name="see-also"></a>Confira também
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)

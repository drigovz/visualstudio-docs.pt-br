---
title: IEnumDebugFields::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b123d1fa644873619d1db512da42031d2ee15ea
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66208050"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
Este método redefine a enumeração para o primeiro elemento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

#### <a name="parameters"></a>Parâmetros
 Nenhum

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Depois que esse método é chamado, a próxima chamada para [próxima](../../../extensibility/debugger/reference/ienumdebugfields-next.md) retorna o primeiro elemento da enumeração.

## <a name="see-also"></a>Consulte também
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [Avançar](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
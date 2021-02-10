---
title: 'IDebugEnumField:: GetUnderlyingSymbol | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c812117e59ca50e64fa6e987ebbe1d30d8d552c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933525"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Esse método retorna um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa o nome da enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parâmetros
`ppField`\
fora Retorna o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que descreve o nome desta enumeração.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O nome da enumeração também contém o tipo da enumeração, que está associada a um local de memória usando o [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="see-also"></a>Confira também
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Associa](../../../extensibility/debugger/reference/idebugbinder-bind.md)

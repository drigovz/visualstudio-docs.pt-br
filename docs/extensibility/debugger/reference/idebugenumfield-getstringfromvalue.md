---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de59c573f7e233ea2aacb0dfa38826051c59373
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730292"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Este método obtém o nome da constante de enumeração dado o seu valor.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>parâmetros
`value`\
[em] O valor para obter o nome da constante de enumeração.

`pbstrValue`\
[fora] Retorna o nome da constante de enumeração.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, `S_FALSE` retorna se o valor não tiver nome associado ou retornar um código de erro.

## <a name="remarks"></a>Comentários
 Se houver mais de um nome associado ao mesmo valor, o primeiro nome definido na enumeração será devolvido.

## <a name="see-also"></a>Confira também
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)

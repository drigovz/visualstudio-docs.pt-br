---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 25becdae62dbdda78e04404528eeb099a4914265
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212398"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Esse método obtém o nome da constante de enumeração recebe seu valor.

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

## <a name="parameters"></a>Parâmetros
`value`\
[in] O valor para o qual obter o nome da enumeração constante.

`pbstrValue`\
[out] Retorna o nome da constante de enumeração.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` se o valor não tem nenhum nome associado ou retorna um código de erro.

## <a name="remarks"></a>Comentários
 Se houver mais de um nome associado com o mesmo valor, o nome definido na enumeração será retornado.

## <a name="see-also"></a>Consulte também
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
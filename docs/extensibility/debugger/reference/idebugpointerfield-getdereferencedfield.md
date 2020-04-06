---
title: IDebugPointerField::GetDeReferencedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 617711a611e6eb1ea162c3abd8ad2b793b4756cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725616"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Este método retorna o tipo de objeto ao qual este objeto ponteiro aponta.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>parâmetros
`ppField`\
[fora] Retorna um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) descrevendo o tipo de objeto de destino.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Se, por exemplo, o objeto [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) apontar para um inteiro, o tipo [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) retornado por este método descreverá esse tipo inteiro.

## <a name="see-also"></a>Confira também
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

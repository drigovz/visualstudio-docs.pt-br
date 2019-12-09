---
title: IDebugField::Equal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8af316c9669b00ae8316888c6a7072d4737dd23d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352661"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Esse método compara esse campo com o campo especificado quanto à igualdade.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Parâmetros
`pField`\
[in] O campo a ser comparado a esta.

## <a name="return-value"></a>Valor de retorno
 Se os campos são os mesmos, retornará `S_OK`. Retorna se os campos forem diferentes, `S_FALSE.` caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
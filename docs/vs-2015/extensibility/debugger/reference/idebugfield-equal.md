---
title: IDebugField::Equal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa630a6f2084f7ff79a9c89b685658cf694fcab9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547306"
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

#### <a name="parameters"></a>Parâmetros
 `pField`

 [in] O campo a ser comparado a esta.

## <a name="return-value"></a>Valor de retorno
 Se os campos são os mesmos, retornará `S_OK`. Retorna se os campos forem diferentes, `S_FALSE.` caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
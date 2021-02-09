---
title: 'IDebugField:: equal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c19e8860fb9ed9cbd65efe7fa72fd920a01622ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915480"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Esse método compara esse campo com o campo especificado para igualdade.

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
no O campo a ser comparado a este.

## <a name="return-value"></a>Valor retornado
 Se os campos forem iguais, retorna `S_OK` . Se os campos forem diferentes, retorna de `S_FALSE.` outra forma, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

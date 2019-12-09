---
title: IDebugObject::IsReadOnly | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21c8a21f3cc85247f1cef4131768984f99fff764
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349950"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Determina se este objeto é somente leitura.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Parâmetros
`pfIsReadOnly`\
[out] Retorna não zero (`TRUE`) se esse objeto é somente leitura; caso contrário, retornará zero (`FALSE`).

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Um objeto somente leitura não pode ter seu valor alterado depois que ele é criado.

## <a name="see-also"></a>Consulte também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
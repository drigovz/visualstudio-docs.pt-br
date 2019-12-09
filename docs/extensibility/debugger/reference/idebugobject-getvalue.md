---
title: IDebugObject::GetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59d58e136045bb4177755c981f91974f9ac2fa77
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323642"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Obtém o valor do objeto consecutivos de bytes.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Parâmetros
`pValue`\
[no, out] Uma matriz que é preenchida com uma série consecutiva de bytes que representa o valor do objeto.

`nSize`\
[in] O número máximo de bytes para buscar.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Obter o número total de bytes do valor que pode ser buscadas chamando o [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) método.

## <a name="see-also"></a>Consulte também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
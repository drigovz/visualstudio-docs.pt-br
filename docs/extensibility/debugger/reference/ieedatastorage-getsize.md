---
title: IEEDataStorage::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81796fe12c72e2e64f1eb1d5b1cc09e66112d13d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319672"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Retorna o número de bytes contidos nesse objeto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>Parâmetros
`size`\
[out] O número de bytes contidos nesse objeto.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Use o [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) método para recuperar os bytes de dados reais.

## <a name="see-also"></a>Consulte também
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
---
title: IEEDataStorage::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eff31ef70fc8cb812ff820a92653b6bb0cab6cd5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868218"
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

#### <a name="parameters"></a>Parâmetros
 `size`

 [out] O número de bytes contidos nesse objeto.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Use o [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) método para recuperar os bytes de dados reais.

## <a name="see-also"></a>Consulte também
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
---
title: 'IEEDataStorage:: GetData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0ff27438ad4a7d0106c1b452f55966dda3f7e07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965558"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Recupera o número especificado de bytes do objeto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>Parâmetros
`dataSize`\
no O número de bytes a serem recuperados (a `data` matriz deve conter pelo menos esse número de bytes).

`sizeGotten`\
fora Retorna o número de bytes realmente recuperados.

`data`\
[entrada, saída] Matriz a ser preenchida com os dados solicitados.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O uso recomendado desse método é recuperar todos os bytes de dados em uma matriz local, já que não há nenhuma maneira de ignorar os bytes no processo de recuperação. Nesse caso, o parâmetro `dataSize` deve ser o valor retornado pelo método [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) .

## <a name="see-also"></a>Confira também
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

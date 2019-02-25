---
title: IDebugArrayObject::GetDimensions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96079e3f82fccc958cc4b9123f8af4227393845f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697020"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Obtém as dimensões da matriz.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

#### <a name="parameters"></a>Parâmetros
 `dwCount`

 [in] O número de dimensões a serem recuperados.

 `dwDimensions`

 [no, out] Uma matriz que é preenchida com os tamanhos de cada dimensão. `dwCount` Especifica o tamanho máximo da `dwDimensions` matriz.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Uma matriz multidimensional pode ter tamanhos diferentes para cada dimensão. Por exemplo, dada a matriz tridimensional `myarray[3][2][6]`, esse método retorna 3, 2 e 6 no `dwDimensions` parâmetro nessa ordem.

## <a name="see-also"></a>Consulte também
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
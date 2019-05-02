---
title: IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fb0d2b960c2bafd1a2d502e41c8a435a5205d11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62865765"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Inicializa os dados de origem para este objeto e retorna um objeto que contém os dados iniciais.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

#### <a name="parameters"></a>Parâmetros
 `dataOut`

 [out] Retorna um [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método faz tudo o que é necessário inicializar um objeto para que ele possa retornar um [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interface nos dados do objeto. Isso permite que os dados do objeto seja exibido e, se puder, alterado por um visualizador de tipo.

## <a name="see-also"></a>Consulte também
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
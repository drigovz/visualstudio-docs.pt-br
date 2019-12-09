---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ce2826aa0bd75638d6f5ee8086cbcce96517ce7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329419"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Atualiza os dados do objeto com o objeto de dados fornecido e retorna um novo objeto de dados que representa os dados do objeto novo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parâmetros
`dataIn`\
[in] Uma [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contém os novos dados.

`dataOut`\
[out] Retorna um novo `IEEDataStorage` objeto que contém os dados substituídos.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Na verdade, esse método atualiza os dados do objeto. Os dados em retornado [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto não precisa ser o mesmo que os dados de entrada `IEEDataStorage` objeto, mas o objeto retornado deve refletir o valor da propriedade atual.

 O objeto de dados de entrada não costuma ser implementado pelo EE. No entanto, o objeto retornado por esse método sempre é implementado pelo EE, que permite que o implemente EE o `IEEDataStorage` interface em qualquer classe for desejada.

 O [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) método cria um objeto de dados com base no objeto de entrada de dados, mas não afeta os dados de original da propriedade.

## <a name="see-also"></a>Consulte também
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
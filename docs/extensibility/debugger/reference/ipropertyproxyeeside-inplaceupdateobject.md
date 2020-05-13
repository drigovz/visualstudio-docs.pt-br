---
title: iPropertyproxyeeside::InplaceUpdateobject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714899"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Atualiza os dados do objeto com o objeto de dados dado e retorna um novo objeto de dados representando os novos dados do objeto.

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

## <a name="parameters"></a>parâmetros
`dataIn`\
[em] Um objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contendo os novos dados.

`dataOut`\
[fora] Retorna um `IEEDataStorage` novo objeto contendo os dados substituídos.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método realmente atualiza os dados do objeto. Os dados do objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) retornado não precisam ser os mesmos que os dados no objeto de entrada, `IEEDataStorage` mas o objeto retornado deve refletir o valor atual da propriedade.

 O objeto de dados de entrada normalmente não é implementado pelo EE. No entanto, o objeto retornado por este método é sempre implementado `IEEDataStorage` pelo EE, que permite ao EE implementar a interface em qualquer classe desejada.

 O método [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) cria um objeto de dados com base no objeto de dados de entrada, mas não afeta os dados originais da propriedade.

## <a name="see-also"></a>Confira também
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)

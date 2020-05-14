---
title: iPropertyProxyEESide::Criarobjeto de substituição | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715033"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Cria uma cópia de um objeto de dados específico do avaliador de expressão (EE).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>parâmetros
`dataIn`\
[em] Um objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que mantém os dados a serem copiados.

`dataOut`\
[fora] Retorna um `IEEDataStorage` novo objeto.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método recebe um objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) representando uma matriz de bytes. Este objeto de dados de entrada normalmente não é implementado pelo EE. No entanto, o objeto retornado por este método é sempre implementado `IEEDataStorage` pelo EE, que permite ao EE implementar a interface em qualquer classe desejada.

 Observe que os dados fornecidos pelo objeto de entrada devem ser os mesmos `IEEDataStorage` dados no objeto de saída. `IEEDataStorage`

## <a name="see-also"></a>Confira também
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

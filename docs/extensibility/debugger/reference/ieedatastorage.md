---
title: IEEDataStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab42216df5c7d5f3d2d349ccf07e595ab3fc616c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335630"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Essa interface representa uma matriz de bytes.

## <a name="syntax"></a>Sintaxe

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O avaliador de expressão (EE) implementa essa interface para representar uma matriz de bytes (usada por visualizadores de tipo para recuperar e alterar dados através de [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface). O EE geralmente implementa essa interface para dar suporte a visualizadores de tipo externo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Os métodos no `IPropertyProxyEESide` interface todas retornar essa interface. Chame [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obter o [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface. Chame [QueryInterface](/cpp/atl/queryinterface) em um [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface para obter o [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 O `IEEDataStorage` interface implementa os métodos a seguir:

|Método|Descrição|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera o número especificado de bytes de dados para um buffer fornecido.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera o número de bytes de dados disponíveis.|

## <a name="remarks"></a>Comentários
 Essa interface é usada por um visualizador de tipo para acessar dados mantidos por um objeto específico. Os dados são tratados como uma matriz de bytes, permitindo que o Visualizador de tipo para manipulá-la de forma que é necessária para apresentá-lo ao usuário.

 Um visualizador personalizado também pode usar essa interface, se desejado, embora mais geral, um visualizador personalizado usa uma interface personalizada, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ou [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (para dados orientados a cadeia de caracteres).

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
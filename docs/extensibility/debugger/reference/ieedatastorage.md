---
title: IEEDataStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbec27d262e43cb0fcdf8317725ad3c77a1817eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966429"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Essa interface representa uma matriz de bytes.

## <a name="syntax"></a>Sintaxe

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão (EE) implementa essa interface para representar uma matriz de bytes (usada pelos visualizadores de tipo para recuperar e alterar dados por meio da interface [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ). O EE normalmente implementa essa interface para oferecer suporte a visualizadores de tipo externo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Todos os métodos na `IPropertyProxyEESide` interface retornam essa interface. Chame [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obter a interface [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Chame [QueryInterface](/cpp/atl/queryinterface) em uma interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) para obter a interface [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A `IEEDataStorage` interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera o número especificado de bytes de dados para um buffer fornecido.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera o número de bytes de dados disponíveis.|

## <a name="remarks"></a>Comentários
 Essa interface é usada por um visualizador de tipo para acessar dados mantidos por um objeto específico. Os dados são tratados como uma matriz de bytes, permitindo que o Visualizador de tipo manipule-o de qualquer maneira necessária para apresentá-lo ao usuário.

 Um visualizador personalizado também pode usar essa interface, se desejado, embora mais geralmente, um visualizador personalizado usaria uma interface personalizada, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ou [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (para dados orientados por cadeia de caracteres).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualizador de tipo e visualizador personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

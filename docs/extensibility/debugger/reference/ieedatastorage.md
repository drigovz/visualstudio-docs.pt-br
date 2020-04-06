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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad7da71d31e1093d87d68bb39958a71a117f5d5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718182"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Esta interface representa uma matriz de bytes.

## <a name="syntax"></a>Sintaxe

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão (EE) implementa essa interface para representar uma matriz de bytes (usado por visualizadores de tipo para recuperar e alterar dados através da interface [IPropertyProxyEESide).](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) O EE normalmente implementa essa interface para suportar visualizadores de tipo externos.

## <a name="notes-for-callers"></a>Observações para chamadores
 Os métodos `IPropertyProxyEESide` na interface retornam esta interface. Ligue para [getPropertyProxyproxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obter a interface [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Chamada [QueryInterface](/cpp/atl/queryinterface) em uma interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) para obter a interface [IPropertyProxyProvider.](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 A `IEEDataStorage` interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera o número especificado de bytes de dados para um buffer fornecido.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera o número de bytes de dados disponíveis.|

## <a name="remarks"></a>Comentários
 Esta interface é usada por um visualizador de tipo para acessar dados mantidos por um objeto específico. Os dados são tratados como uma matriz de bytes, permitindo que o visualizador do tipo os manipule da maneira que for necessário para apresentá-los ao usuário.

 Um visualizador personalizado também pode usar essa interface, se desejar, embora mais tipicamente, um visualizador personalizado usaria uma interface personalizada, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ou [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (para dados orientados a strings).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

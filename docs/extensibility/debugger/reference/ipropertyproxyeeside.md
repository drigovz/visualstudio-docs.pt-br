---
title: IPropertyProxyeeside | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89cecbf22091a45e31c307c5b523ac8aa4c924e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714853"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Esta interface fornece métodos para visualizar dados sobre o objeto associado. Esta interface faz parte do suporte para visualizadores de tipo.

## <a name="syntax"></a>Sintaxe

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um avaliador de expressão implementa essa interface para suportar visualizadores de tipo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para [getPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obter essa interface. Chamada [QueryInterface](/cpp/atl/queryinterface) em uma interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) para obter a interface [IPropertyProxyProvider.](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 Os seguintes métodos são implementados por esta interface:

|Método|Descrição|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicializa um provedor de origem de dados para que os dados do objeto possam ser acessados.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Recupera informações sobre a montagem do objeto.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Obtém os dados iniciais do objeto.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Cria uma cópia de um armazenamento de dados existente.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Cria uma referência a um armazenamento de dados existente.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Recupera informações sobre um conjunto específico no contexto da montagem que contém este objeto.|

## <a name="remarks"></a>Comentários
 Um visualizador de tipo usa essa interface para acessar os valores associados ao objeto do qual essa interface faz parte. Os dados são acessados através da interface [IEEDataStorage,](../../../extensibility/debugger/reference/ieedatastorage.md) que fornece uma exibição somente de leitura dos dados.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

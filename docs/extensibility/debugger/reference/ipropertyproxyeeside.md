---
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd9b804556cd748c921a0c21729daee56e9499b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708453"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Essa interface fornece métodos para exibir dados sobre o objeto associado. Essa interface é parte do suporte para visualizadores de tipo.

## <a name="syntax"></a>Sintaxe

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um avaliador de expressão implementa essa interface para dar suporte a visualizadores de tipo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chame [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obter essa interface. Chame [QueryInterface](/cpp/atl/queryinterface) em um [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface para obter o [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Os métodos a seguir são implementados por esta interface:

|Método|Descrição|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicializa um provedor de fonte de dados para que os dados do objeto podem ser acessados.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Recupera informações sobre o assembly do objeto.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Obtém os dados iniciais para o objeto.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Cria uma cópia de um armazenamento de dados existente.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Cria uma referência para um armazenamento de dados existente.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Recupera informações sobre um assembly específico no contexto do assembly que contém este objeto.|

## <a name="remarks"></a>Comentários
 Um visualizador de tipo usa essa interface para acessar os valores associados com o objeto que esta interface é parte do. Os dados são acessados por meio de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interface, que fornece uma exibição somente leitura dos dados.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
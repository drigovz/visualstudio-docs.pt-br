---
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71d993c7f99cade5b866e67298132a325986e3a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714789"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Esta interface fornece uma interface proxy para visualizar e alterar os dados de um objeto.

## <a name="syntax"></a>Sintaxe

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão (EE) implementa essa interface no mesmo objeto que implementa a interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) como parte do suporte do EE a visualizadores de tipo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para o `IDebugProperty3` [QueryInterface](/cpp/atl/queryinterface) em uma interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 A `IPropertyProxyProvider` interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera uma interface proxy de propriedade para visualizar dados em um objeto.|

## <a name="remarks"></a>Comentários
 Embora o EE implemente essa interface, a implementação do [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) é normalmente tratada pelo [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Consulte [Visualização e visualização de dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes sobre a obtenção da interface IEEVisualizerService.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Visualizar e exibir dados](../../../extensibility/debugger/visualizing-and-viewing-data.md)

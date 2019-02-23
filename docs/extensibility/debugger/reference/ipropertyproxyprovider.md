---
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1e9afbe99e6265e47bf033c7d4af8e93590aaf6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718248"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Essa interface fornece uma interface de proxy para exibir e alterar dados de um objeto.

## <a name="syntax"></a>Sintaxe

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O avaliador de expressão (EE) implementa essa interface no mesmo objeto que implementa o [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface como parte do suporte do EE dos visualizadores de tipo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chame [QueryInterface](/cpp/atl/queryinterface) em um `IDebugProperty3` interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 O `IPropertyProxyProvider` interface implementa o método a seguir:

|Método|Descrição|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera uma interface de proxy de propriedade para exibir dados em um objeto.|

## <a name="remarks"></a>Comentários
 Embora o EE implementa essa interface, a implementação de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) normalmente é manipulada por [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Ver [visualização e exibindo os dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes sobre como obter a interface IEEVisualizerService.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Visualizar e exibir dados](../../../extensibility/debugger/visualizing-and-viewing-data.md)
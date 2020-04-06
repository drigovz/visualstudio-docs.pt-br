---
title: IEEVisualizerService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40d21dcc9b1da0e1e2250adcfad59b3ef46a2113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717933"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interface implementa métodos-chave que fornecem funcionalidade para as interfaces [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) e [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)

## <a name="syntax"></a>Sintaxe

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O Visual Studio implementa essa interface para permitir que um avaliador de expressão (EE) suporte visualizadores de tipo.

## <a name="notes-for-callers"></a>Observações para chamadores
 O EE chama [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) para obter essa interface como parte de seu suporte para visualizadores de tipo.

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable

|Método|Descrição|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Recupera o número de espectadores personalizados sobre os quais este serviço sabe.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Recupera a lista de espectadores personalizados.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Retorna um objeto proxy para uma propriedade.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Recupera o número de strings de valor a serem exibidas para a propriedade ou campo especificado.|

## <a name="remarks"></a>Comentários
 O IDE usa a interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) para determinar se há visualizadores personalizados ou visualizadores de digitações para a propriedade. Ao criar um serviço de visualização (com [CreateVisualizerService),](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)o `IDebugProperty3` EE pode fornecer a funcionalidade para as interfaces [iPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (que suporta a visualização e alteração do valor de uma propriedade) e, assim, suporte visualizadores de tipo.

 Se um EE tiver visualizadores personalizados que implemente, o EE poderá anexar os `CLSID`s desses espectadores personalizados ao final da lista retornada pelo [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Isso permite que um EE suporte tanto visualizadores de tipo quanto seus próprios espectadores personalizados. Apenas certifique-se de que [getCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) reflete a adição de qualquer espectador personalizado.

 Consulte [Visualizador de tipo e visualizador personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) para uma discussão sobre a diferença entre visualizadores e espectadores.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

---
title: IEEVisualizerDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718058"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interface fornece a capacidade de alterar o valor de um objeto através de um visualizador de tipo.

## <a name="syntax"></a>Sintaxe

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão implementa essa interface para suportar a modificação de dados em um objeto de propriedade através de um visualizador de tipo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é usada para criar o objeto [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) através de uma chamada para [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Consulte [Visualização e Visualização de Dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter mais detalhes.

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable

|Método|Descrição|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Determina se é possível atualizar o objeto (e, posteriormente, seu valor) que este visualizador está representando.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Força uma reavaliação do objeto para este visualizador.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtém um objeto existente para este visualizador (nenhuma avaliação é feita).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Atualiza o objeto para este visualizador, alterando assim o valor que o visualizador apresenta.|

## <a name="remarks"></a>Comentários
 O serviço de visualização (representado pela interface [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) e retornado pelo [CreateVisualizerService)](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)mantém uma referência ao objeto que implementa a `IEEVisualizerDataProvider` interface. Como resultado, `IEEVisualizerDataProvider` a interface não deve ser implementada no mesmo objeto que implementa o [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) se esse objeto mantiver uma referência ao `IEEVisualizerService` objeto: uma referência circular resulta e um impasse ocorre quando os objetos são destruídos. A abordagem recomendada `IEEVisualizerDataProvider` é implementar em um `IDebugProperty2` objeto separado `IUnknown::AddRef` ao qual o objeto delega sem chamá-lo.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Visualizar e exibir dados](../../../extensibility/debugger/visualizing-and-viewing-data.md)

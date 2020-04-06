---
title: Implementando visualizadores de tipo e espectadores personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738501"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementar visualizadores de tipo e visualizadores personalizados
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Os visualizadores de digitação e os visualizadores personalizados permitem que um usuário visualize dados de um determinado tipo de uma maneira que seja mais significativa do que um simples despejo hexadecimal de números. Um avaliador de expressão (EE) pode associar espectadores personalizados a tipos específicos de dados ou variáveis. Esses espectadores personalizados são implementados pelo EE. O EE também pode suportar visualizadores de tipo externos, que podem vir de outro fornecedor de terceiros ou até mesmo do usuário final.

## <a name="discussion"></a>Discussão

### <a name="type-visualizers"></a>Visualizadores de tipo
 O Visual Studio pede uma lista de visualizadores de tipo e espectadores personalizados para que cada objeto seja exibido em uma janela do relógio. Um avaliador de expressão (EE) fornece tal lista para cada tipo para o qual deseja suportar visualizadores de tipo e espectadores personalizados. Chamadas para [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) iniciam todo o processo de acessando visualizadores de tipos e visualizadores personalizados (consulte [Visualizando e Visualizando Dados](../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes sobre a seqüência de chamadas).

### <a name="custom-viewers"></a>Espectadores personalizados
 Os visualizadores personalizados são implementados no EE para um tipo de dados específico e são representados pela interface [IDebugCustomViewer.](../../extensibility/debugger/reference/idebugcustomviewer.md) Um visualizador personalizado não é tão flexível quanto um visualizador de tipo, já que ele só está disponível quando o EE que implementa esse visualizador personalizado em particular está executando. Implementar um visualizador personalizado é mais simples do que implementar suporte para visualizadores de tipo. No entanto, os visualizadores de tipo de suporte dão a máxima flexibilidade ao usuário final para visualizar seus dados. O restante desta discussão diz respeito apenas a visualizadores de tipo.

## <a name="interfaces"></a>Interfaces
 O EE implementa as seguintes interfaces para suportar visualizadores de tipo, a serem consumidos pelo Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  O EE consome as seguintes interfaces para suportar visualizadores de tipo:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Confira também
- [Escrevendo um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualização e visualização de dados](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)

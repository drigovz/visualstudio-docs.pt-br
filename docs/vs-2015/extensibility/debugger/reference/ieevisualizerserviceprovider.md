---
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c9ba7c7216c590f773f1054a1f06cd3412ff6b20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838396"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface fornece acesso a um método que pode criar um serviço visualizador, que é usado para tratar tarefas de visualizador de tipo para o IDE.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O Visual Studio implementa essa interface para criar um objeto de serviço do visualizador que, por sua vez, é usado para fornecer IDs `CLSID` de classe dos visualizadores de tipo para o IDE do Visual Studio.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O avaliador de expressão (EE) chama [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Cria o serviço Visualizador|  
  
## <a name="remarks"></a>Comentários  
 A `IEEVisualizerServiceProvider` interface é obtida durante a implementação de [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). O serviço visualizador que essa interface cria é usado para fornecer funcionalidade a uma interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , que o EE é responsável por implementar. O EE também é responsável pela implementação de uma interface [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) que permite que os visualizadores de tipos exibam e modifiquem o valor de uma propriedade.  
  
 Consulte [visualizando e exibindo dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes sobre como essas interfaces interagem.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Visualizando e exibindo dados](../../../extensibility/debugger/visualizing-and-viewing-data.md)

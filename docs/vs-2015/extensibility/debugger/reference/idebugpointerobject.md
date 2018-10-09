---
title: IDebugPointerObject | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 217136135c7fec71065f6a18e156ff2e5e956499
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476370"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugPointerObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerobject).  
  
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface representa um objeto de ponteiro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O avaliador de expressão implementa essa interface para representar um objeto de ponteiro.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface pode obter essa interface usando [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) se o `IDebugObject` representa um ponteiro.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Além dos métodos herdados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), o `IDebugPointerObject` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Desreferenciar](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Obtém o objeto para o qual a interface aponta.|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Obtém o valor para o qual a interface aponta como uma série de bytes consecutivos.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Define o valor para o qual a interface aponta de uma série de bytes consecutivos.|  
  
## <a name="remarks"></a>Comentários  
 Um avaliador de expressão usa essa interface para representar um ponteiro em uma árvore de análise.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

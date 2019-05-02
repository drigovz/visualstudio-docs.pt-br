---
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: be39e42de029b597d46fc775ef7df63c5d31c0c1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439057"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface permite que o avaliador de expressão (EE) para chamar métodos ou propriedades em instâncias de classe de valor (por exemplo, `System.Decimal`) e para definir seu valor sem chamar [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) sobre o programa que está sendo depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um avaliador de expressão implementa essa interface para representar um objeto de código gerenciado, como uma variável.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Para obter essa interface, chame [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) em um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa uma instância de uma classe de valor.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Além dos métodos herdados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), o `IDebugManagedObject` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Retorna uma interface que representa o objeto de código gerenciado e de que qualquer código gerenciado apropriado interface pode ser obtido.|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Define o valor desse objeto para o valor de um objeto de código gerenciado especificado.|  
  
## <a name="remarks"></a>Comentários  
 Um avaliador de expressão usa essa interface para armazenar um objeto de código gerenciado em uma árvore de análise.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Avaliar](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)

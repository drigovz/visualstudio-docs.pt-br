---
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fbd270aa1b65f05f308d41d22f154fb53b8833d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727685"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface permite que o avaliador de expressão (EE) chame propriedades `System.Decimal`ou métodos em instâncias de classe de valor (por exemplo, ) e defina seu valor sem chamar [Avaliar](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) sobre o programa que está sendo depurado.

## <a name="syntax"></a>Sintaxe

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um avaliador de expressão implementa essa interface para representar um objeto de código gerenciado, como uma variável.

## <a name="notes-for-callers"></a>Observações para chamadores
 Para obter essa interface, chame [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) em um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa uma instância de uma classe de valor.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos herdados do [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md)a `IDebugManagedObject` interface expõe os seguintes métodos.

|Método|Descrição|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Retorna uma interface que representa o objeto de código gerenciado e a partir do qual qualquer interface de código gerenciada apropriada pode ser obtida.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Define o valor deste objeto para o valor de um objeto de código gerenciado especificado.|

## <a name="remarks"></a>Comentários
 Um avaliador de expressão usa essa interface para armazenar um objeto de código gerenciado em uma árvore de análise.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Avaliar](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)

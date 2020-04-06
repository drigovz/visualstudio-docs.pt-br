---
title: IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6433c1f2c540b040a3b3beccc264377e69592387
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728494"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interface representa uma função.

## <a name="syntax"></a>Sintaxe

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um avaliador de expressão implementa essa interface para representar uma função.

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface é uma especialização da interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) e é `IDebugObject` obtida usando [o QueryInterface](/cpp/atl/queryinterface) na interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos herdados do [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md)a `IDebugFunctionObject` interface expõe os seguintes métodos.

|Método|Descrição|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Cria um objeto de dados primitivo.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Cria um objeto usando um construtor.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Cria um objeto sem construtor.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Cria um objeto de matriz.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Cria um objeto de seqüência.|
|[Avaliar](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Chama a função e retorna o valor resultante como um objeto.|

## <a name="remarks"></a>Comentários
 Esta interface permite que o avaliador de expressão represente funções em uma árvore de análise. Os `Create` métodos nesta interface são usados para construir objetos que representam os parâmetros de entrada para o método. A função pode então ser executada chamando o método [Avaliar,](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) que retorna um objeto representando o valor de retorno da função.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

---
title: IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97fd6c328b15c8e41dbbc2b4e45bfc4285b4273f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319022"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface representa um objeto que o associador cria para encapsular os valores de símbolos e expressões.

## <a name="syntax"></a>Sintaxe

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um avaliador de expressão implementa essa interface para representar um objeto.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é a classe base para todos os objetos que o avaliador de expressão usa expressões analisado. Ele é retornado por uma chamada para o [associar](../../../extensibility/debugger/reference/idebugbinder-bind.md) método. [QueryInterface](/cpp/atl/queryinterface) obtém as interfaces mais especializadas dessa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugObject`.

|Método|Descrição|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Obtém o tamanho do objeto.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Obtém o valor do objeto consecutivos de bytes.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Define o valor do objeto de uma série consecutiva de bytes.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Define o valor de referência do objeto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Obtém o contexto de memória que representa o endereço do valor do objeto.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Cria uma cópia do objeto gerenciado no espaço de endereço do mecanismo de depuração.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Testa se este objeto é uma referência nula.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Compara um objeto para esse outro.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Determina se este objeto é somente leitura.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Determina se o objeto for um proxy transparente.|

## <a name="remarks"></a>Comentários
 O avaliador de expressão usa essa interface como a classe base para representar objetos em uma árvore de análise.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Avaliação de Expressões](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Associar](../../../extensibility/debugger/reference/idebugbinder-bind.md)
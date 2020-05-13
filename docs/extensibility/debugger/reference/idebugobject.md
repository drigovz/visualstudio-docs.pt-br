---
title: IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726304"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interface representa um objeto que o fichário cria para encapsular os valores de símbolos e expressões.

## <a name="syntax"></a>Sintaxe

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um avaliador de expressão implementa essa interface para representar um objeto.

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface é a classe base para todos os objetos que o avaliador de expressão usa em expressões parsed. É devolvido por uma chamada para o método [Bind.](../../../extensibility/debugger/reference/idebugbinder-bind.md) [QueryInterface](/cpp/atl/queryinterface) obtém as interfaces mais especializadas desta interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugObject`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Fica com o tamanho do objeto.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Obtém o valor do objeto como uma série consecutiva de bytes.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Define o valor do objeto a partir de uma série consecutiva de bytes.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Define o valor de referência deste objeto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Obtém o contexto de memória que representa o endereço do valor do objeto.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Cria uma cópia do objeto gerenciado no espaço de endereço do mecanismo de depuração.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Testa se esse objeto é uma referência nula.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Compara um objeto com este.|
|[Isreadonly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Determina se esse objeto é somente leitura.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Determina se o objeto é um proxy transparente.|

## <a name="remarks"></a>Comentários
 O avaliador de expressão usa essa interface como classe base para representar objetos em uma árvore de análise.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Associar](../../../extensibility/debugger/reference/idebugbinder-bind.md)

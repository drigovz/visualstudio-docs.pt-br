---
title: IDebugReference2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720267"
---
# <a name="idebugreference2"></a>IDebugReference2
Esta interface representa uma referência a uma propriedade de quadro de pilha ou alguma outra propriedade.

> [!NOTE]
> `IDebugReference2`é reservado para uso futuro, e `E_NOTIMPL`todos os seus métodos devem retornar .

## <a name="syntax"></a>Sintaxe

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O DE implementa essa interface para representar uma referência a um determinado tipo de valor. Por exemplo, o valor pode ser um valor numérico como resultado de uma avaliação de expressão, um contexto de memória usado para exibir memória ou uma lista de registros e seus valores.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para [getReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) para obter esta interface. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) e [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) também retornam essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugReference2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Obtém a [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estrutura que descreve essa referência.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Define o valor desta referência a partir de uma seqüência de string.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Define o valor desta referência a partir de outra referência.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Enumera as crianças desta referência.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Fica com o pai desta referência.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Obtém a referência mais derivada desta referência.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Obtém os bytes de memória aos quais esta referência se refere.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Obtém um contexto de memória para esta referência.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Obtém o tamanho, em bytes, desta referência.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Define este tipo de referência.|
|[Comparar](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Compara essa referência com outra.|

## <a name="remarks"></a>Comentários

> [!NOTE]
> Esse uso de "propriedade" não deve ser confundido com esse `IDebugReference2` significado de uma variável membro de uma classe, embora possa representar tal entidade.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) representa uma propriedade, enquanto `IDebugReference2` representa uma referência a uma propriedade, tipicamente uma referência a um objeto no programa que está sendo depurado.

 A principal diferença entre uma propriedade e uma referência é que uma propriedade se refere a uma instância nomeada de um objeto, enquanto uma referência refere-se a uma instância não nomeada. Por exemplo, uma propriedade pode se referir a `"a.b"`um objeto no monte do programa por . Outra propriedade pode se referir `"c.d"`ao mesmo objeto que . A maneira de se referir `"a.b"` a `"c.d"` esta propriedade requer isso ou estar no escopo. Uma referência a este mesmo objeto é sem nome; o objeto pode ser referido desde que a memória desse objeto seja válida.

 Uma `IDebugProperty2` interface pode ser considerada como um valor com um nome, um tipo e um endereço. Um `IDebugReference2`, por outro lado, pode ser pensado como um tipo e um endereço.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [Getreference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)

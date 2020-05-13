---
title: IDebugProperty2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b04abdac135143ccbbd1b8e5632bf85c974f29d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721231"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Esta interface representa uma propriedade de quadro de pilha, uma propriedade de documento de programa ou alguma outra propriedade. A propriedade é geralmente o resultado de uma avaliação de expressão.

> [!NOTE]
> Esse uso de "propriedade" não deve ser confundido com esse `IDebugProperty2` significado de uma variável membro de uma classe, embora possa representar tal entidade.

## <a name="syntax"></a>Sintaxe

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O DE implementa essa interface para representar um determinado tipo de valor. Por exemplo, o valor pode ser um valor numérico como resultado de uma avaliação de expressão, um contexto de memória usado para exibir memória ou uma lista de registros e seus valores.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chamar [AssessSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [AssessAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obter essa interface, o que representa o resultado de uma avaliação. `IDebugExpression2::EvaluateAsync`retorna esta interface enviando uma interface [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) para o SDM, que por sua vez chama [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) para recuperar a propriedade.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) retorna esta interface para fornecer o documento de script associado.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) retorna esta interface para representar o valor de retorno de uma função.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) retorna esta interface para representar várias propriedades do programa, como um nome ou um contexto de memória.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) retorna esta interface para representar várias propriedades do quadro de pilha, como variáveis locais.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugProperty2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Getpropertyinfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Preenche uma estrutura [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) que descreve uma propriedade.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Define o valor de uma propriedade a partir de uma seqüência.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Define o valor da propriedade a partir do valor de uma determinada referência.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Enumera os filhos de uma propriedade.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Devolve o pai de uma propriedade.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Devolve a propriedade que descreve a propriedade mais derivada de uma propriedade.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Retorna os bytes de memória que compõem o valor de uma propriedade.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Retorna o contexto de memória para um valor de propriedade.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Devolve o tamanho, em bytes, do valor da propriedade.|
|[Getreference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Retorna uma referência ao valor desta propriedade.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Retorna as informações estendidas de uma propriedade.|

## <a name="remarks"></a>Comentários
 Uma propriedade, representada `IDebugProperty2` por uma interface, pode ser considerada como um valor com um nome, um tipo e um endereço. Em termos mais gerais, pode `IDebugProperty2` representar qualquer coisa que tenha uma estrutura hierárquica, com nós pais e filhos.

 Uma propriedade geralmente é transitória, durando apenas o tempo que o quadro de pilha atual, por exemplo. Por outro lado, uma referência, representada por uma interface [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) dura enquanto o valor permanece na memória.

 O IDE pode `IDebugProperty2` usar a interface para permitir que os usuários naveguem e modifiquem propriedades em tempo de execução.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

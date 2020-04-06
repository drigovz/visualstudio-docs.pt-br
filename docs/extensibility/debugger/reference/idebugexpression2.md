---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2e23ad4f673e4e150ea677d993c5b36a4e386c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729693"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Esta interface representa uma expressão parsed pronta para vinculação e avaliação.

## <a name="syntax"></a>Sintaxe

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa esta interface para representar uma expressão parsed pronta para ser avaliada.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) retorna esta interface. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retorna a interface [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Essas interfaces só são acessíveis quando o programa que está sendo depurado foi pausado e um quadro de pilha está disponível.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugExpression2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Avalia essa expressão assíncronamente.|
|[Abortar](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina a avaliação de expressão assíncrona.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Avalia essa expressão sincronicamente.|

## <a name="remarks"></a>Comentários
 Quando um programa é interrompido, o SDM (Session Debug Manager, gerenciador de depuração de sessão) obtém um quadro de pilha do DE com uma chamada para [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). O SDM então chama [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter a interface [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Isso é seguido por uma chamada para `IDebugExpression2` [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para criar a interface, que representa a expressão parsed pronta para ser avaliada.

 O SDM chama [O AssessSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [o AssessAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para realmente avaliar a expressão e produzir um valor.

 Em uma `IDebugExpressionContext2::ParseText`implementação de , `CoCreateInstance` o DE usa a função DO COM para instanciar um avaliador de expressão e obter uma interface [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (veja o Exemplo na `IDebugExpressionEvaluator` interface). Em seguida, o DE chama [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obter uma interface [IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Esta interface é utilizada `IDebugExpression2::EvaluateSync` na `IDebugExpression2::EvaluateAsync` implementação e realização da avaliação.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)

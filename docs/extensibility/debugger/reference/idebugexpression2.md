---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8027f34b48b4a160c19f14f0d9cbfb8194a506f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919977"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Essa interface representa um pronto de expressão analisada para avaliar e associação.

## <a name="syntax"></a>Sintaxe

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração (DES) implementa essa interface para representar uma expressão analisada pronta para ser avaliada.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) retorna essa interface. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retorna o [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Essas interfaces são acessíveis somente quando o programa que está sendo depurado foi pausado e um quadro de pilha está disponível.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugExpression2`.

|Método|Descrição|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Avalia essa expressão de forma assíncrona.|
|[Anular](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina a avaliação da expressão assíncrona.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Avalia essa expressão de forma síncrona.|

## <a name="remarks"></a>Comentários
 Quando um programa foi interrompida, o Gerenciador de sessão de depuração (SDM) obtém um quadro de pilha de com uma chamada para [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Em seguida, chama o SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter o [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Isso é seguido por uma chamada para [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para criar o `IDebugExpression2` interface, que representa a expressão analisada pronta para ser avaliada.

 O SDM chama o [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , na verdade, avaliar a expressão e produzir um valor.

 Em uma implementação de `IDebugExpressionContext2::ParseText`, o DE usa do COM `CoCreateInstance` função para instanciar um avaliador de expressão e obter uma [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interface (consulte o exemplo a `IDebugExpressionEvaluator` interface). Em seguida, chama o DE [analisar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obter uma [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) interface. Essa interface é usada na implementação de `IDebugExpression2::EvaluateSync` e `IDebugExpression2::EvaluateAsync` para executar a avaliação.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
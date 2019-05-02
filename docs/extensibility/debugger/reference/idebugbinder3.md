---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a08ee3f637b954d2df7e48fb8f6aebbdd0948c19
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414070"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface fornece acesso aos tipos, aliases e serviços do visualizador personalizado.

## <a name="syntax"></a>Sintaxe

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um mecanismo de depuração implementa essa interface para dar suporte a aliases, serviços de visualizador personalizado e acesso a informações de tipo de objeto.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface obtém essa interface usando [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos fornecidos pelo [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface, essa interface implementa o seguinte:

|Método|Descrição|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Recupera um objeto de memória que representa a memória para o qual este objeto está associado.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Recupera a exceção associada a esse objeto (se houver),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Recupera um dado seu nome de alias|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Recupera uma matriz de todos os aliases para este objeto|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Obtém o número de tipos de argumento associado a este objeto|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Recupera uma lista de tipos de argumento associado a este objeto|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Obtém uma interface para um serviço de Visualizador|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Converte um local do objeto ou um endereço de memória de 64 bits em um contexto de memória.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Avaliação de Expressões](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
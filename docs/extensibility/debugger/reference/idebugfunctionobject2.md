---
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 304269ba2a4f556cfe931157c445d7b4fc86f489
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929934"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa uma função e aprimora a interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="syntax"></a>Sintaxe

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um avaliador de expressão (EE) implementa essa interface para representar uma função.

## <a name="notes-for-callers"></a>Observações para chamadores
 Os métodos dessa interface adiam os de **IDebugFunctionObject** das seguintes maneiras:

- O método **IDebugEvaluate** usa sinalizadores.

- O método **CreateObject** usa sinalizadores e um tempo limite.

- O método **CreateStringObjectWithLength** usa um comprimento.

## <a name="methods"></a>Métodos
 Essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Cria um objeto que usa um construtor de acordo com as configurações de sinalizador de avaliação e um valor de tempo limite.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Cria um objeto de cadeia de caracteres que tem o comprimento especificado.|
|[Avaliar](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Chama a função e retorna o valor resultante como um objeto.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

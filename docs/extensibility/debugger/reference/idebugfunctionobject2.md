---
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc54c235dc0366d0e120b0ab1cb087e0d00ca741
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413820"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa uma função e aprimora a [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.

## <a name="syntax"></a>Sintaxe

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um avaliador de expressão (EE) implementa essa interface para representar uma função.

## <a name="notes-for-callers"></a>Observações para chamadores
 Métodos dessa interface adiar aqueles **IDebugFunctionObject** das seguintes maneiras:

- O **IDebugEvaluate** método usa sinalizadores.

- O **CreateObject** método usa um tempo limite e sinalizadores.

- O **CreateStringObjectWithLength** método usa um comprimento.

## <a name="methods"></a>Métodos
 Essa interface implementa os métodos a seguir:

|Método|Descrição|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Cria um objeto que usa um construtor que recebe as configurações de sinalizador de avaliação e um valor de tempo limite.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Cria um objeto de cadeia de caracteres que tem o comprimento especificado.|
|[Avaliar](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Chama a função e retorna o valor resultante como um objeto.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: EE.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
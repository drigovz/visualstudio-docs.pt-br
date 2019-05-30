---
title: IDebugAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29b7a8bca687ff2992c5e3fb92cb0cc6c8a1740d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338133"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa um alias de numérico para uma variável. Um alias é simplesmente um nome diferente para uma variável.

## <a name="syntax"></a>Sintaxe

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O avaliador de expressão (EE) implementa essa interface para dar suporte a aliases numéricos para variáveis.

## <a name="notes-for-callers"></a>Observações para chamadores
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) cria um alias para um determinado objeto. Para procurar os aliases, use [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) ou [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Os métodos a seguir são definidos na `IDebugAlias` interface.

|Método|Descrição|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Obtém o objeto ao qual esse alias se refere.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Obtém o nome do alias.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Recupera um `ICorDebugValue` gerenciado de interface que fornece acesso a informações de código sobre esse objeto (somente código gerenciado).|
|[Descartar](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Marca este alias como não mais que está sendo usado.|

## <a name="remarks"></a>Comentários
 Um alias é um número decimal no formulário de cadeia de caracteres seguido pelo caractere #, por exemplo, # 1001.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Avaliação de Expressões](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
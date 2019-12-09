---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3f027fd08c38433d5f1357e56d90df96e223854
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317257"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface fornece informações adicionais sobre um objeto.

## <a name="syntax"></a>Sintaxe

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O avaliador de expressão implementa essa interface para oferecer suporte a aliases e acesso a informações sobre o objeto.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface pode obter essa interface usando [QueryInterface](/cpp/atl/queryinterface). Além disso, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) retorna essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos na [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface, o `IDebugObject2` interface implementa o seguinte:

|Método|Descrição|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtém o campo ou variável (se houver) que pode ser fazendo a propriedade representada por este objeto.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtém o objeto de código gerenciado que representa o valor desse objeto.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Cria uma ID exclusiva para esse objeto ou retorna um alias existente.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Obtém o alias associado com esse objeto, se houver.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtém o tipo desse objeto.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina se este objeto representa dados de usuário.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina se o estado de editar e continuar não é válido.<br /><br /> Um avaliador de expressão personalizada não implementa esse método (ele deve sempre retornar `E_NOTIMPL`).|

## <a name="remarks"></a>Comentários
 Ver [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) para uma discussão sobre aliases.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Avaliação de Expressões](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
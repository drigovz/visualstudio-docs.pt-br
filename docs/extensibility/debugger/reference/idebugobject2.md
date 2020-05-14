---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468b5a282ffb5466d57a3c9b1a37aa3ae8643ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726079"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interface fornece informações adicionais sobre um objeto.

## <a name="syntax"></a>Sintaxe

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão implementa essa interface para oferecer suporte para aliases e acesso a informações sobre o objeto.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) pode obter essa interface usando [o QueryInterface](/cpp/atl/queryinterface). Além disso, [o GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) retorna esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 Além dos métodos na interface [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) a `IDebugObject2` interface implementa o seguinte:

|Método|Descrição|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtém o campo ou variável (se houver) que pode estar apoiando a propriedade representada por este objeto.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtém o objeto de código gerenciado representando o valor deste objeto.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Cria um ID exclusivo para este objeto ou retorna um alias existente.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Obtém o alias associado a este objeto, se houver.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtém o tipo deste objeto.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina se esse objeto representa os dados do usuário.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina se o estado Editar e Continuar não é mais válido.<br /><br /> Um avaliador de expressão personalizado não implementa `E_NOTIMPL`este método (ele deve sempre retornar ).|

## <a name="remarks"></a>Comentários
 Consulte [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) para uma discussão sobre pseudônimos.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)

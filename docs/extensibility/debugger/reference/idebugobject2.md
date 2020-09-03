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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726079"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface fornece informações adicionais sobre um objeto.

## <a name="syntax"></a>Syntax

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão implementa essa interface para oferecer suporte a aliases e acesso a informações sobre o objeto.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) pode obter essa interface usando [QueryInterface](/cpp/atl/queryinterface). Além disso, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) retorna essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Além dos métodos na interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , a `IDebugObject2` interface implementa o seguinte:

|Método|Descrição|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtém o campo ou variável (se houver) que pode estar fazendo backup da propriedade representada por esse objeto.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtém o objeto de código gerenciado que representa o valor deste objeto.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Cria uma ID exclusiva para esse objeto ou retorna um alias existente.|
|[Getalias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Obtém o alias associado a este objeto, se houver.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtém o tipo deste objeto.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina se este objeto representa dados do usuário.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina se o estado de edição e continuação não é mais válido.<br /><br /> Um avaliador de expressão personalizado não implementa esse método (ele sempre deve retornar `E_NOTIMPL` ).|

## <a name="remarks"></a>Comentários
 Consulte [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) para obter uma discussão sobre aliases.

## <a name="requirements"></a>Requisitos
 Cabeçalho: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)

---
title: IDebugAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2ceb87277460f65e52c35f02e7fbbd01da1101a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736519"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa um pseudônimo numérico para uma variável. Um pseudônimo é simplesmente um nome diferente para uma variável.

## <a name="syntax"></a>Sintaxe

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão (EE) implementa essa interface para suportar aliases numéricas para variáveis.

## <a name="notes-for-callers"></a>Observações para chamadores
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) cria um alias para um determinado objeto. Para procurar pseudônimos, use [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) ou [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Os seguintes métodos `IDebugAlias` são definidos na interface.

|Método|Descrição|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Obtém o objeto ao qual este pseudônimo se refere.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Tem o nome do pseudônimo.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Recupera uma `ICorDebugValue` interface que fornece acesso a informações de código gerenciadas sobre este objeto (somente código gerenciado).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Marca este pseudônimo como não sendo mais usado.|

## <a name="remarks"></a>Comentários
 Um alias é um número decimal em forma de string seguido pelo caractere #, por exemplo, 1001#.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)

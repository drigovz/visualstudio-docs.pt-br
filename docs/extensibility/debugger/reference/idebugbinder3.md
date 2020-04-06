---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa85872337fdc1f7519d0de98cffe1436ef41c67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735673"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface fornece acesso a tipos, aliases e serviços de visualização personalizados.

## <a name="syntax"></a>Sintaxe

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um mecanismo de depuração implementa essa interface para dar suporte a aliases, serviços de visualização personalizados e acesso a informações do tipo de objeto.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma interface [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obtém essa interface usando [o QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 Além dos métodos fornecidos pela interface [IDebugBinder,](../../../extensibility/debugger/reference/idebugbinder.md) esta interface implementa o seguinte:

|Método|Descrição|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Recupera um objeto de memória representando a memória à qual este objeto está vinculado.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Recupera a exceção associada a este objeto (se houver),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Recupera um pseudônimo dado seu nome,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Recupera uma matriz de todos os pseudônimos para este objeto,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Obtém o número de tipos de argumentoassociados a este objeto,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Recupera uma lista de tipos de argumentoassociados a este objeto,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Obtém uma interface para um serviço de visualizador,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Converte um local de objeto ou um endereço de memória de 64 bits em um contexto de memória.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)

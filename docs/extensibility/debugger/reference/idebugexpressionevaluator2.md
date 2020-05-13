---
title: IDebugExpressionAvaliaor2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7041456bf0f3ae7930a73399d43dbf7cac6b3b32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729148"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa uma versão aprimorada de um avaliador de expressão (EE).

## <a name="syntax"></a>Sintaxe

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esta interface é implementada por um avaliador de expressão.

## <a name="methods"></a>Métodos
 Além dos métodos na interface [IDebugExpressionEvaluator,](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Recupera um objeto de serviço dado seu identificador único.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Pré-carrega os módulos designados pelo provedor de símbolos especificado.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Habilita o avaliador de expressão (EE) para especificar a interface de retorno de chamada que o mecanismo de depurador (DE) usará para ler as configurações métricas.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Define o caminho para o tempo de execução do idioma comum (CLR) carregado no depurador.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Permite que um mecanismo de depuração passe um retorno de chamada para o avaliador de expressão durante a inicialização.|
|[Encerrar](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Pára e limpa o avaliador de expressão.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

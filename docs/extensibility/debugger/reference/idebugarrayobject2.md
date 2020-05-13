---
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a6580d0cbdead7866bbc6dd106a2aa0ea56f76
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736229"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa um objeto de matriz gerenciado e permite que um avaliador de expressão (EE) determine o índice base (limites inferiores) para a matriz.

## <a name="syntax"></a>Sintaxe

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Isso é implementado pelo motor de depuração gerenciado (DE).

## <a name="methods"></a>Métodos
 Além dos métodos na interface [IDebugArrayObject,](../../../extensibility/debugger/reference/idebugarrayobject.md) esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Recupera os índices base (limites inferiores) para cada índice dado o número de dimensões na matriz.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Determina se a matriz tem índices base (limites inferiores) definidos.|

## <a name="remarks"></a>Comentários
 Um avaliador de expressão usa essa interface para representar matrizes gerenciadas em uma árvore de análise.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

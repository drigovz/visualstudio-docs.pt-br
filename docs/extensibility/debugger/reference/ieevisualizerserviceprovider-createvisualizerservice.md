---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e05677122b7d4e4eb025a9382ede1509374de894
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717911"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Este método cria um serviço de visualização.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>parâmetros
`binder`\
[em] O objeto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) passou para [AssessSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
[em] O objeto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) passou para `IDebugParsedExpression::EvaluateSync`.

`pAddress`\
[em] O objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) passou para `IDebugParsedExression::EvaluateSync`.

`dataProvider`\
[em] Um objeto que implementa a interface [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (fornecida pelo avaliador de expressão).

`ppService`\
[fora] O serviço criado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 `pSymProv`Todos `binder`os `pAddress` parâmetros foram passados para o `IDebugParsedExpression::EvaluateSync` método. `CreateVisualizerService`deve ser chamado `IDebugParsedExpression::EvaluateSync` apenas a partir de como parte do suporte de um avaliador de expressão para visualizadores de tipo.

## <a name="see-also"></a>Confira também
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

---
title: IDebugBinder3::GetEEService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c08d7df4a6b05be489f6b9ab06569c085f3b1f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735831"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Este método retorna um serviço solicitado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>parâmetros
`vendor`\
[em] `GUID` de um fornecedor (um valor nulo é aceitável).

`language`\
[em] `GUID` de uma língua (um valor nulo é aceitável).

`iid`\
[em] `IID` do serviço para obter.

`ppService`\
[fora] Uma interface para o serviço solicitado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Passe `IID` para a interface [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) (`IID_IEEVisualizerServiceProvider`) para ver se o serviço Type Visualizer está disponível. Nesse caso, o avaliador de expressão pode obter a interface [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) para suportar visualizadores de tipo. Consulte [Visualização e Visualização de Dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes.

## <a name="see-also"></a>Confira também
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualizar e exibir dados](../../../extensibility/debugger/visualizing-and-viewing-data.md)

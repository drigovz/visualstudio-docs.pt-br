---
title: IEEVisualizerService::GetCustomViewerCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerCount
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerCount method
ms.assetid: f7b095c2-e538-4352-8cad-d4c6d4f6bdbc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 750094cef6e207ef1a77196dab53b28ebdc7838b
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223648"
---
# <a name="ieevisualizerservicegetcustomviewercount"></a>IEEVisualizerService::GetCustomViewerCount
Esse método obtém o número de visualizadores de tipo disponíveis desse serviço.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCustomViewerCount(
   ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parâmetros
 `pcelt`\

 [out] Retorna o número de visualizadores de tipo disponíveis.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) passa a solicitação para este método em seu suporte para visualizadores de tipo.

## <a name="see-also"></a>Consulte também
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
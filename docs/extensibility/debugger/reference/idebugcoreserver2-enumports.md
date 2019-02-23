---
title: IDebugCoreServer2::EnumPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::EnumPorts
helpviewer_keywords:
- IDebugCoreServer2::EnumPorts
ms.assetid: 3d98dfd0-614f-4d68-90c6-8a9b9cab66f1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bafa89a38d008a54536976097edc2a874d1ba2d3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686269"
---
# <a name="idebugcoreserver2enumports"></a>IDebugCoreServer2::EnumPorts
Recupera uma lista de todas as portas disponíveis.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumPorts( 
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPorts( 
   out IEnumDebugPorts2 ppEnum
);
```

#### <a name="parameters"></a>Parâmetros
 `ppEnum`

 [out] Retorna um [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) objeto que contém uma lista de todas as portas de todos os fornecedores de porta.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
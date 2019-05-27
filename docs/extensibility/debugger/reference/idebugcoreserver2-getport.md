---
title: IDebugCoreServer2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 578826eba2cd89ba045590ae110f57949e572064
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205646"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Recupera uma porta específica.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Parâmetros
`guidPort`\
[in] GUID da porta a ser recuperado.

`ppPort`\
[out] Retorna um [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa a porta desejada.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Retorna `E_PORTSUPPLIER_NO_PORT` se não houver nenhuma porta com o identificador fornecido.

## <a name="see-also"></a>Consulte também
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
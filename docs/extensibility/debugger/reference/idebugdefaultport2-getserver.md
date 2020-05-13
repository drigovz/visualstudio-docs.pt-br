---
title: IDebugDefaultPort2:GetServer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3dbe6d813b85865b0fdbc20296473684203a3f1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732378"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Este método obtém uma interface para o servidor em que esta porta está.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>parâmetros
`ppServer`\
[fora] Retorna um objeto que implementa a interface [IDebugCoreServer3.](../../../extensibility/debugger/reference/idebugcoreserver3.md)

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) é implementado pelo Visual Studio e representa o servidor em que a porta está localizada.

## <a name="see-also"></a>Confira também
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

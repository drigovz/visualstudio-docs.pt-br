---
title: IDebugEngine2::SetLocale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8616dd827f99dfcfbc337cb5cdf5ac5a7d392e88
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730908"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Define a localização do motor de depuração (DE).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

## <a name="parameters"></a>parâmetros
`wLangID`\
[em] Especifica o local do idioma. Por exemplo, 1033 para inglês.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método é chamado pelo Gerenciador de depuração de sessão (SDM) para propagar as configurações de localização do IDE para que as strings retornadas pelo DE sejam devidamente localizadas.

## <a name="see-also"></a>Confira também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

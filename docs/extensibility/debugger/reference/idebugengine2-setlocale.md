---
title: 'IDebugEngine2:: setlocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e43d8d13f34b8477ab870c80842ff33eef72a7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878910"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Define a localidade do mecanismo de depuração (DE).

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

## <a name="parameters"></a>Parâmetros
`wLangID`\
no Especifica a localidade do idioma. Por exemplo, 1033 para inglês.

## <a name="return-value"></a>Valor de retorno
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é chamado pelo SDM (Gerenciador de depuração de sessão) para propagar as configurações de localidade do IDE para que as cadeias de caracteres retornadas por sejam localizadas corretamente.

## <a name="see-also"></a>Confira também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

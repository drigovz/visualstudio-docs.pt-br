---
title: 'IDebugSymbolProviderDirect:: GetAppIDFromAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetAppIDFromAddress
- GetAppIDFromAddress
ms.assetid: d76a0f36-79c4-4c58-9db3-880b00d11610
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfdc81b18b68a3dafe239bb2f23f700f9796cf8e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909559"
---
# <a name="idebugsymbolproviderdirectgetappidfromaddress"></a>IDebugSymbolProviderDirect::GetAppIDFromAddress
Recupera o identificador de domínio do aplicativo de acordo com o endereço de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetAppIDFromAddress(
   IDebugAddress* pAddress,
   DWORD*         pAppID
);
```

```csharp
int GetAppIDFromAddress(
   IDebugAddress pAddress,
   out uint      pAppID
);
```

## <a name="parameters"></a>Parâmetros
`pAddress`\
no Endereço de depuração que é representado pela interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pAppID`\
fora Identificador do domínio do aplicativo.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)

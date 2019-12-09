---
title: IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba0675038a495a91755794d7e43ad57cfc7d438a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326946"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Recupera um nome amigável para o servidor.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parâmetros
`pbstrName`\
[out] Retorna um nome amigável para o servidor.

> [!NOTE]
> O chamador é responsável por liberar a cadeia de caracteres.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.

## <a name="remarks"></a>Comentários
 Para servidores iniciado pelo usuário, o nome retornado por esse método é o nome completo do servidor. Para servidores iniciado automaticamente, o nome é que, da máquina, o servidor está executando no.

 Para um nome orientado por máquina, chame o [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) método.

## <a name="see-also"></a>Consulte também
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
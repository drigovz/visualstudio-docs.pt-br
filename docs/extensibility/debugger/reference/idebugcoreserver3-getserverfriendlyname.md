---
title: IDebugCoreServer3:GetServerFriendlyName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eec30783041a1240d8f85815c06f4ca60729a484
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732889"
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

## <a name="parameters"></a>parâmetros
`pbstrName`\
[fora] Retorna um nome amigável para o servidor.

> [!NOTE]
> O interlocutor é responsável por liberar a seqüência.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro.

## <a name="remarks"></a>Comentários
 Para servidores iniciados pelo usuário, o nome retornado por este método é o nome completo do servidor. Para servidores lançados automaticamente, o nome é o da máquina em que o servidor está sendo executado.

 Para obter um nome orientado à máquina, chame o método [GetServerName.](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)

## <a name="see-also"></a>Confira também
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [Obternome de servidor](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)

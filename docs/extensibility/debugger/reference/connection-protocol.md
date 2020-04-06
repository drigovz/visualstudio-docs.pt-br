---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737641"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Indica o protocolo que está sendo usado para se comunicar entre um servidor de depuração e o pacote de depuração (DE).

## <a name="syntax"></a>Sintaxe

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Campos
`CONNECTION_NONE`\
Nenhuma conexão foi feita a um servidor.

`CONNECTION_UNKNOWN`\
Uma conexão foi feita, mas é de um tipo desconhecido.

`CONNECTION_LOCAL`\
A conexão é com um servidor local.

`CONNECTION_PIPE`\
A conexão é através de um tubo chamado.

`CONNECTION_TCPIP`\
A conexão usa TCP/IP.

`CONNECTION_HTTP`\
A conexão usa HTTP (através de um servidor Web).

`CONNECTION_OTHER`\
Algum outro tipo de conexão foi estabelecida (esse valor não é usado atualmente).

## <a name="remarks"></a>Comentários
Esses valores são devolvidos a partir do método [GetConnectionProtocol.](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)

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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d25068b71689ffbc9e472addbd6ca3663db267c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891274"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Indica o protocolo que está sendo usado para comunicação entre um servidor de depuração e o pacote DE depuração (DE).

## <a name="syntax"></a>Sintaxe

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Campos
`CONNECTION_NONE`\
Nenhuma conexão foi feita com um servidor.

`CONNECTION_UNKNOWN`\
Uma conexão foi feita, mas é de um tipo desconhecido.

`CONNECTION_LOCAL`\
A conexão é para um servidor local.

`CONNECTION_PIPE`\
A conexão é por meio de um pipe nomeado.

`CONNECTION_TCPIP`\
A conexão usa TCP/IP.

`CONNECTION_HTTP`\
A conexão usa HTTP (por meio de um servidor Web).

`CONNECTION_OTHER`\
Algum outro tipo de conexão foi estabelecido (esse valor não é usado no momento).

## <a name="remarks"></a>Comentários
Esses valores são retornados do método [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)

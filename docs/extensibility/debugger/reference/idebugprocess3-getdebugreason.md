---
title: 'IDebugProcess3:: GetDebugReason | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetDebugReason
helpviewer_keywords:
- IDebugProcess3::GetDebugReason
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2fa12b74b44761761a08e232a9f3efa845fa73a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723670"
---
# <a name="idebugprocess3getdebugreason"></a>IDebugProcess3::GetDebugReason
Esse método retorna o motivo pelo qual o processo foi iniciado para depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDebugReason(
   DEBUG_REASON* pReason
);
```

```csharp
int GetDebugReason(
   out enum_DEBUG_REASON pReason
);
```

## <a name="parameters"></a>Parâmetros
`pReason`\
fora Retorna um valor da enumeração [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) .

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro.

## <a name="see-also"></a>Confira também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)

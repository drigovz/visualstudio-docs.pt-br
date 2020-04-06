---
title: IDebugProcess3::GetENCAvailableState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77345cfc3aa1dd95482052893e7c09591ad7cd4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723648"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Este método obtém o estado atual de Editar e Continuar do processo. Um fornecedor de porto personalizado deve sempre retornar `E_NOTIMPL`.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>parâmetros
`pReason`\
[fora] Um valor da [enumeração EncUnavailableReason.](../../../extensibility/debugger/reference/encunavailablereason.md)

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro.

> [!NOTE]
> Um fornecedor de porto personalizado deve sempre retornar `E_NOTIMPL`.

## <a name="remarks"></a>Comentários
 Este estado pode ser afetado por [DisablENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).

## <a name="see-also"></a>Confira também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)

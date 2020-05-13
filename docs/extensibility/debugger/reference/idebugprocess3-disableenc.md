---
title: IDebugProcess3::DisableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b39bb448501bacd5ab458b7e61bb1a5044bc8a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723737"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Este método desativa explicitamente Editar e Continuar neste processo (e todos os programas que ele contém). Um fornecedor de porto personalizado deve sempre retornar `E_NOTIMPL`.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>parâmetros
`reason`\
[em] Um valor da [enumeração EncUnavailableReason.](../../../extensibility/debugger/reference/encunavailablereason.md)

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro.

> [!NOTE]
> Um fornecedor de porto personalizado deve sempre retornar `E_NOTIMPL`.

## <a name="remarks"></a>Comentários
 Uma vez que editar e continuar estiver desativado para um processo, ele só poderá ser reativado reiniciando o processo.

## <a name="see-also"></a>Confira também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)

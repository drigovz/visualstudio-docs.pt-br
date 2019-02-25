---
title: IDebugProcess3::DisableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39b7456d9a045331c53f8465cc7387823c734104
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688921"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Esse método explicitamente desabilita editar e continuar sobre esse processo (e todos os programas que ele contém). Um fornecedor de porta personalizado deve sempre retornar `E_NOTIMPL`.

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

#### <a name="parameters"></a>Parâmetros
 `reason`

 [in] Um valor a partir de [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) enumeração.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.

> [!NOTE]
>  Um fornecedor de porta personalizado deve sempre retornar `E_NOTIMPL`.

## <a name="remarks"></a>Comentários
 Uma vez editar e continuar está desabilitado para um processo, ele pode ser habilitado novamente reiniciando o processo.

## <a name="see-also"></a>Consulte também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
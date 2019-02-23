---
title: IDebugEngine2::GetEngineID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 842d78a2ea2ff665102b9cef922f463baf53cb78
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698840"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
Obtém o GUID do mecanismo de depuração (DES).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

#### <a name="parameters"></a>Parâmetros
`pguidEngine`

 [out] Retorna o GUID do DE.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Alguns exemplos de GUIDs típicos `guidScriptEng`, `guidNativeEng`, ou `guidSQLEng`. Novos mecanismos de depuração criará seu próprio GUID para identificação.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como implementar esse método para um simples `CEngine` objeto que implementa o [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interface.

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>Consulte também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

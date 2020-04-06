---
title: IDebugCodeContext3::GetProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3::GetProcess
ms.assetid: e082e494-2255-4d9d-a5a9-6dadd904bea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d169f86548e97d4bb745e1ba91f39782de97cbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734179"
---
# <a name="idebugcodecontext3getprocess"></a>IDebugCodeContext3::GetProcess
Recupera uma referência à interface do processo de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetProcess(
    IDebugProcess2 **ppProcess
);
```

```csharp
public int GetProcess(
    out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>parâmetros
`ppProcess`\
[fora] Referência à interface do processo de depuração.

## <a name="return-value"></a>Valor retornado
Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como implementar esse método para um objeto **CDebugCodeContext** que expõe a interface [IDebugBeforeSymbolSearchEvent2.](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)

```cpp
HRESULT CDebugCodeContext::GetProcess(IDebugProcess2** ppProcess)
{
    HRESULT hr = S_OK;
    CComPtr<CDebugEngine> pEngine;
    CComPtr<IDebugPort2> pPort2;

    IfFalseGo( ppProcess, E_INVALIDARG );
    *ppProcess = NULL;

    IfFalseGo( m_pProgram, E_FAIL );
    IfFailGo( ((CDebugProgram *)m_pProgram)->GetEngine(&pEngine) );
    IfFailGo( pEngine->GetSDMProcess(ppProcess) );

Error:

    return hr;
}
```

## <a name="see-also"></a>Confira também
- [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)

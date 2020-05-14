---
title: FRAMEINFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736789"
---
# <a name="frameinfo"></a>FRAMEINFO
Descreve um quadro de pilha.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>Membros
`m_dwValidFields`\
Uma combinação de bandeiras da enumeração [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) que especifica quais campos são preenchidos.

`m_bstrFuncName`\
O nome da função associado ao quadro de pilha.

`m_bstrReturnType`\
O tipo de retorno associado ao quadro de pilha.

`m_bstrArgs`\
Os argumentos para a função associada ao quadro de pilha.

`m_bstrLanguage`\
A linguagem em que a função é implementada.

`m_bstrModule`\
O nome do módulo associado ao quadro de pilha.

`m_addrMin`\
O endereço mínimo de pilha física.

`m_addrMAX`\
O endereço máximo da pilha física.

`m_pFrame`\
O objeto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que representa este quadro de pilha.

`m_pModule`\
O objeto [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que representa o módulo que contém este quadro de pilha.

`m_fHasDebugInfo`\
Não-zero`TRUE`( ) se existir informações de depuração no quadro dado.

`m_fStaleCode`\
Não-zero`TRUE`( ) se o quadro de pilha estiver associado a um código que não é mais válido.

`m_fAnnotatedFrame`\
Não-zero`TRUE`( ) se o quadro de pilha for anotado pelo gerenciador de depuração de sessão (SDM).

## <a name="remarks"></a>Comentários
Essa estrutura é passada para o método [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) a ser preenchido. Essa estrutura também está contida em uma lista contida na interface [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) que, por sua vez, é retornada de uma chamada para o método [EnumFrameInfo.](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

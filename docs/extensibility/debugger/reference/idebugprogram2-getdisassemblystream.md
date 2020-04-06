---
title: IDebugProgram2::GetDisassemblyStream | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2160f963ad1f3f37291519ced30b8096e33a6116
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722871"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Obtém o fluxo de desmontagem para este programa ou uma parte deste programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>parâmetros
`dwScope`\
[em] Especifica um valor da enumeração [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) que define o escopo do fluxo de desmontagem.

`pCodeContext`\
[em] Um objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa a posição de onde iniciar o fluxo de desmontagem.

`ppDisassemblyStream`\
[fora] Retorna um objeto [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) que representa o fluxo de desmontagem.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Retorna `E_DISASM_NOTSUPPORTED` se a desmontagem não for suportada para esta arquitetura em particular.

## <a name="remarks"></a>Comentários
 Se `dwScopes` o parâmetro `DSS_HUGE` tiver a bandeira do conjunto de enumeração [DISASSEMBLY_STREAM_SCOPE,](../../../extensibility/debugger/reference/disassembly-stream-scope.md) espera-se que a desmontagem retorne um grande número de instruções de desmontagem, por exemplo, para um arquivo ou módulo inteiro. Se `DSS_HUGE` a bandeira não for definida, espera-se que a desmontagem seja limitada a uma pequena região, tipicamente a de uma única função.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)

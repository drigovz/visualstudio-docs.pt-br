---
title: IDebugDisassemblyStream2:GetCodeLocationId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32be70e11776177a0e68f09689c2262497703ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732247"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Retorna um identificador de localização de código para um contexto de código específico.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>parâmetros
`pCodeContext`\
[em] Um objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) a ser convertido em um identificador.

`puCodeLocationId`[fora] Retorna o identificador de localização do código. Consulte Observações.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Retorna `E_CODE_CONTEXT_OUT_OF_SCOPE` se o contexto de código for válido, mas fora do escopo.

## <a name="remarks"></a>Comentários
 O identificador de localização de código é específico para o mecanismo de depuração (DE) que suporta a desmontagem. Este identificador de localização é usado internamente pelo DE para rastrear posições no código e é tipicamente um endereço ou deslocamento de algum tipo. O único requisito é que se o contexto de código de um local for menor do que o contexto de código de outro local, então o identificador de localização de código correspondente do primeiro contexto de código também deve ser menor do que o identificador de localização de código do segundo contexto de código.

 Para recuperar o contexto de código de um identificador de localização de código, chame o método [GetCodeContext.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

## <a name="see-also"></a>Confira também
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

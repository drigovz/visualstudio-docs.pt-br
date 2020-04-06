---
title: IDebugProgram2::EnumCodePaths | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723039"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Recupera uma lista dos caminhos de código para uma determinada posição em um arquivo de origem.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>parâmetros
`pszHint`\
[em] A palavra sob o cursor na exibição **Origem** ou **Desmontagem** no IDE.

`pStart`\
[em] Um objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) representando o contexto de código atual.

`pFrame`\
[em] Um objeto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) representando o quadro de pilha associado ao ponto de ruptura atual.

`fSource`\
[em] Não zero`TRUE`( ) se na exibição **Origem,** ou zero (`FALSE`) se na exibição **Desmontagem.**

`ppEnum`\
[fora] Retorna um objeto [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) contendo uma lista dos caminhos de código.

`ppSafety`\
[fora] Retorna um objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) representando um contexto de código adicional a ser definido como um ponto de ruptura no caso de o caminho de código escolhido ser ignorado. Isso pode acontecer no caso de uma expressão booleana de curto-circuito, por exemplo.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um caminho de código descreve o nome de um método ou função que foi chamado para chegar ao ponto atual na execução do programa. Uma lista de caminhos de código representa a pilha de chamadas.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)

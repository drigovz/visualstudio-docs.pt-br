---
title: IDebugProgram2::EnumCodePaths | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09437fddf5cd61aef06341494431c747c4c66c8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870529"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Recupera uma lista dos caminhos de código para uma posição especificada em um arquivo de origem.

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

#### <a name="parameters"></a>Parâmetros
 `pszHint`

 [in] A palavra sob o cursor na **fonte** ou **desmontagem** exibição no IDE.

 `pStart`

 [in] Uma [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa o contexto de código atual.

 `pFrame`

 [in] Uma [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) representando o quadro de pilha associado com o ponto de interrupção atual do objeto.

 `fSource`

 [in] Diferente de zero (`TRUE`) se estiver na **código-fonte** modo de exibição, ou zero (`FALSE`) se estiver no **desmontagem** exibição.

 `ppEnum`

 [out] Retorna um [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) objeto que contém uma lista de caminhos de código.

 `ppSafety`

 [out] Retorna um [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) do objeto que representa um contexto de código adicional a ser definido como um ponto de interrupção no caso de caminho de código a escolhida será ignorada. Isso pode acontecer no caso de uma expressão booliana curto-circuitada, por exemplo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um caminho de código descreve o nome de um método ou função que foi chamada para chegar ao ponto atual na execução do programa. Uma lista de caminhos de código representa a pilha de chamadas.

## <a name="see-also"></a>Consulte também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
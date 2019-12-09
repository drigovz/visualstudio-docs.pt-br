---
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 25ac9881f44019d818c49091900ce759680a37a5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319072"
---
# <a name="bplocationcodefuncoffset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Descreve o local de deslocamento de um ponto de interrupção em uma função no código.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {
    BSTR                     bstrContext;
    IDebugFunctionPosition2* pFuncPos;
} BP_LOCATION_CODE_FUNC_OFFSET;
```

## <a name="members"></a>Membros
`bstrContext`\
O contexto do ponto de interrupção, normalmente um nome de método ou função, como visto em uma pilha de chamadas.

`pFuncPos`\
O [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) objeto que descreve o nome da função e a posição relativa do início da função.

## <a name="remarks"></a>Comentários
Essa estrutura é um membro do [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estrutura como parte de uma união.

O `pFuncPos` membro indica onde definir o ponto de interrupção de função.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)

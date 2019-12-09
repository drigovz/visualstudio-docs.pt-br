---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: cf8e2958f55ca13ab050302a24ad9e5ae185d81a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353087"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
Usada para definir pontos de interrupção de dados se baseiam em uma cadeia de caracteres que o usuário pode inserir do ambiente de desenvolvimento integrado (IDE).

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Membros
`pThread`\
O [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread em que o ponto de interrupção ocorre.

`bstrContext`\
O contexto do ponto de interrupção dentro do código, geralmente, um nome de método ou função, como visto em uma pilha de chamadas.

`bstrDataExpr`\
A cadeia de caracteres de dados que o usuário insere para definir o ponto de interrupção.

`dwNumElements`\
O número de elementos na cadeia de caracteres de dados no qual o ponto de interrupção ocorre.

## <a name="remarks"></a>Comentários
Essa estrutura é um membro do [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estrutura como parte de uma união.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

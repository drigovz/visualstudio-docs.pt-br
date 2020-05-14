---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 75f881feaaa2068abd98d771a63024f20435d98f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737975"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Usado para definir pontos de interrupção de dados baseados em uma seqüência que o usuário pode inserir a partir do ambiente de desenvolvimento integrado (IDE).

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
O objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o segmento no qual ocorre o ponto de ruptura.

`bstrContext`\
O contexto do ponto de ruptura dentro do código, tipicamente um método ou nome de função como visto em uma pilha de chamadas.

`bstrDataExpr`\
A seqüência de dados que o usuário entra para definir o ponto de ruptura.

`dwNumElements`\
O número de elementos na seqüência de dados em que ocorre o ponto de ruptura.

## <a name="remarks"></a>Comentários
Essa estrutura é membro da estrutura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de um sindicato.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

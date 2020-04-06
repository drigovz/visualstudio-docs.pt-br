---
title: IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 732eadc955b9a6c9bdded3d52f038ff58ed9c217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725684"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Define ou altera a contagem de passes associada ao ponto de ruptura pendente.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>parâmetros
`bpPassCount`\
[em] Uma estrutura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que contém a contagem de passes.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o ponto de ruptura tiver sido excluído.

## <a name="remarks"></a>Comentários
 Qualquer contagem de passes que tenha sido anteriormente associada ao ponto de ruptura pendente é perdida. Todos os pontos de interrupção vinculados a partir deste `bpPassCount` ponto de interrupção pendente são chamados para definir sua contagem de passes para o parâmetro.

## <a name="see-also"></a>Confira também
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)

---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfb8a39af3c030dadddcb148a79a96b57f20e183
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721883"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Anexa-se ao programa associado ou adia o processo de anexação ao método [Anexar.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>parâmetros
`guidProgramId`\
[em] `GUID` para atribuir ao programa associado.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se o método [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md) não for chamado. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Este método é chamado durante o processo de anexação, antes que o método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) seja chamado. O `OnAttach` método pode realizar o próprio processo de `S_FALSE`conexão (nesse caso, `IDebugEngine2::Attach` esse método `OnAttach` retorna) ou adiar o processo de anexação ao método (o método retorna `S_OK`). Em ambos os `OnAttach` casoes, `GUID` o método pode definir o `GUID`programa que está sendo depurado para o dado .

## <a name="see-also"></a>Confira também
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)

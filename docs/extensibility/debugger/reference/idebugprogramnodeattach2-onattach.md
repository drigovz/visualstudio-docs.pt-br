---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79f15102b5adae2112f4abdeeb68b80962895e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916793"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Anexa ao programa associado ou adia o processo de anexação para o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.

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

#### <a name="parameters"></a>Parâmetros
 `guidProgramId`

 [in] `GUID` para atribuir ao programa associado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método não deve ser chamado. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é chamado durante o processo de anexação, antes de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método é chamado. O `OnAttach` método pode executar o processo de anexação (nesse caso, esse método retorna `S_FALSE`) ou adiar o processo de anexação para o `IDebugEngine2::Attach` método (o `OnAttach` retorno do método `S_OK`). Em ambos os casos, o `OnAttach` método pode definir o `GUID` do programa que está sendo depurado a determinado `GUID`.

## <a name="see-also"></a>Consulte também
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
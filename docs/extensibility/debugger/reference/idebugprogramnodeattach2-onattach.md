---
title: 'IDebugProgramNodeAttach2:: onattach | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721883"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Anexa ao programa associado ou adia o processo de anexação para o método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

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

## <a name="parameters"></a>Parâmetros
`guidProgramId`\
[in] `GUID` para atribuir ao programa associado.

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se o método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) não deve ser chamado. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é chamado durante o processo de anexo, antes que o método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) seja chamado. O `OnAttach` método pode executar o processo de anexo em si (nesse caso, esse método retorna `S_FALSE` ) ou adiar o processo de anexação para o `IDebugEngine2::Attach` método (o `OnAttach` método retorna `S_OK` ). Em qualquer evento, o `OnAttach` método pode definir o `GUID` do programa que está sendo depurado para o determinado `GUID` .

## <a name="see-also"></a>Confira também
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)

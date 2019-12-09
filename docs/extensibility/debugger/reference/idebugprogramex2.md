---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13a9e44ee2a7782cb804c4e0b6f4279918e7d78e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325100"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Essa interface permite que a sessão de depuração SDM (Gerenciador) anexar a um programa e colocar o nó de programa associado com um programa.

## <a name="syntax"></a>Sintaxe

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um fornecedor de porta personalizada implementa essa interface no mesmo objeto como o [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface para permitir que o SDM anexar a um programa enquanto ao mesmo tempo permitindo que o fornecedor de porta acompanhar todas as sessões anexado a programa. O fornecedor de porta personalizada pode implementar essa interface se optar por.

## <a name="notes-for-callers"></a>Observações para chamadores
 As chamadas SDM [QueryInterface](/cpp/atl/queryinterface) em um `IDebugProgram2` interface para obter essa interface para rastrear as sessões que anexados aos programas.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugProgramEx2`.

|Método|Descrição|
|------------|-----------------|
|[Anexar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Anexa um programa para uma sessão.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtém o nó de programa associado com um programa.|

## <a name="remarks"></a>Comentários
 Essa interface é privada entre o SDM e o programa.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
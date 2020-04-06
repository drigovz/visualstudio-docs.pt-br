---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722337"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Esta interface permite que o Gerenciador de depuração de sessão (SDM) seja anexado a um programa e obtenha o nó do programa associado a um programa.

## <a name="syntax"></a>Sintaxe

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um fornecedor de porta personalizado implementa essa interface no mesmo objeto da interface [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) a fim de permitir que o SDM seja anexado a um programa e, ao mesmo tempo, permitir que o fornecedor de portas acompanhe todas as sessões anexadas ao programa. O fornecedor de porta personalizado pode implementar esta interface se quiser.

## <a name="notes-for-callers"></a>Observações para chamadores
 O SDM chama [queryInterface](/cpp/atl/queryinterface) em uma `IDebugProgram2` interface para obter esta interface para rastrear sessões que foram anexadas a programas.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugProgramEx2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Anexa um programa a uma sessão.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Tem o nó do programa associado a um programa.|

## <a name="remarks"></a>Comentários
 Esta interface é privada entre o SDM e o programa.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

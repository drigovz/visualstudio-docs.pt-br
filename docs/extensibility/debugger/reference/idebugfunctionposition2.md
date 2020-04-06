---
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c260b6316207b0079a2ca8893b851db8b1288ba6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728313"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Esta interface representa uma posição abstrata de uma função em um documento de origem.

## <a name="syntax"></a>Sintaxe

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface para representar a posição de uma função dentro de um documento de origem.

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface é fornecida como parte de uma [união BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (especificamente, uma estrutura [BP_LOCATION_CODE_FUNC_OFFSET)](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) que, por sua vez, faz parte da estrutura [BP_REQUEST_INFO,](../../../extensibility/debugger/reference/bp-request-info.md) usada na criação de um ponto de ruptura pendente.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugFunctionPosition2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Obtém o nome da função a que esta posição é relativa.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Obtém o deslocamento desde o início da função.|

## <a name="remarks"></a>Comentários
 A posição representada por essa interface é baseada em texto, especificamente, uma estrutura [TEXT_POSITION.](../../../extensibility/debugger/reference/text-position.md)

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

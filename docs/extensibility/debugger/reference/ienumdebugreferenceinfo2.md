---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 14b5bdc8a8be5734da765f0396fb96830042969f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842219"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Essa interface enumera estruturas de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .

## <a name="syntax"></a>Sintaxe

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface como parte de seu suporte para referências a objetos na memória. Essa interface deve ser implementada somente se houver suporte para referências.

## <a name="notes-for-callers"></a>Observações para chamadores
 O Visual Studio chama [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A tabela a seguir mostra os métodos de `IEnumDebugReferenceInfo2` .

|Método|Descrição|
|------------|-----------------|
|[Próximo](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Recupera um número especificado de estruturas de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) em uma sequência de enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Ignora um número especificado de estruturas de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) na sequência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[8i](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Obtém o número de estruturas de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) em um enumerador.|

## <a name="remarks"></a>Comentários
 Uma referência é essencialmente um tipo e um endereço, enquanto que uma propriedade é um nome, tipo e endereço. Uma referência persiste, desde que o objeto referido exista na memória. Consulte [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) para obter mais detalhes.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)

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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6132235a7e4789c7d9efe5bae9d7fd531112dab4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715276"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Esta interface enumera [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estruturas.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface como parte de seu suporte para referências a objetos na memória. Esta interface só deve ser implementada se as referências forem suportadas.

## <a name="notes-for-callers"></a>Observações para chamadores
 O Visual Studio chama [a EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IEnumDebugReferenceInfo2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Recupera um número especificado de [estruturas DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) em uma seqüência de enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Salta um número especificado de [estruturas DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) na seqüência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Reinicia uma seqüência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Obtém o número de [estruturas DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) em um enumerador.|

## <a name="remarks"></a>Comentários
 Uma referência é essencialmente um tipo e um endereço, enquanto uma propriedade é um nome, tipo e endereço. Uma referência persiste enquanto o objeto referido existir na memória. Consulte [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) para obter mais detalhes.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)

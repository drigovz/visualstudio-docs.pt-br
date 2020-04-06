---
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715347"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Esta interface enumera [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estruturas.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface para representar informações para uma determinada propriedade.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para a [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obter esta interface representando os filhos de uma propriedade específica. Ligue para [enumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) para obter esta interface representando as propriedades de um quadro de pilha específico.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IEnumDebugPropertyInfo2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Recupera um número especificado de estruturas [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) em uma seqüência de enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Salta um número especificado de [estruturas DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) em uma seqüência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Reinicia uma seqüência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Obtém o número de [estruturas DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) em um enumerador.|

## <a name="remarks"></a>Comentários
 Em geral, uma propriedade é uma hierarquia de informações que pode incluir um nome, valor, endereço e tipo, bem como quaisquer outras informações apropriadas ao objeto de propriedade associado ou quadro de pilha. Consulte [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) para obter mais detalhes.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)

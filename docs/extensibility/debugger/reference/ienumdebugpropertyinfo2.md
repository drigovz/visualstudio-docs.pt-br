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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ecbb7db381261e1c836b48994eb0f208b619b3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842206"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Essa interface enumera estruturas de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .

## <a name="syntax"></a>Sintaxe

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface para representar informações para uma determinada propriedade.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chame [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obter essa interface representando os filhos de uma propriedade específica. Chame [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) para obter essa interface representando as propriedades de um determinado registro de ativação.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A tabela a seguir mostra os métodos de `IEnumDebugPropertyInfo2` .

|Método|Descrição|
|------------|-----------------|
|[Próximo](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Recupera um número especificado de estruturas de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) em uma sequência de enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Ignora um número especificado de estruturas de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) em uma sequência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[8i](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Obtém o número de estruturas de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) em um enumerador.|

## <a name="remarks"></a>Comentários
 Em geral, uma propriedade é uma hierarquia de informações que pode incluir um nome, valor, endereço e tipo, bem como qualquer outra informação apropriada ao objeto de propriedade ou ao quadro de pilha associado. Consulte [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) para obter mais detalhes.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)

---
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31133139d0104cd29f5d0d0e760bd78ec5783fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732685"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Essa interface representa um atributo personalizado e pode fornecer o nome, o pai e o tipo de classe do atributo.

## <a name="syntax"></a>Sintaxe

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um provedor de símbolos implementa essa interface para suportar atributos personalizados associados a um símbolo. É tipicamente implementado em seu próprio objeto.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para [o Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) retorna esta interface. Uma chamada para o método [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) retorna a interface [IEnumDebugCustomAttributes.](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugCustomAttribute`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Obtém o campo ao qual o atributo atual está anexado.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Obtém o tipo de classe de atributo personalizado.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Obtém o nome do atributo personalizado.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Obtém a informação do atributo como uma bolha de bytes.|

## <a name="remarks"></a>Comentários
 Um atributo personalizado é uma estrutura para C# que fornece metadados personalizados associados a uma determinada classe ou método.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

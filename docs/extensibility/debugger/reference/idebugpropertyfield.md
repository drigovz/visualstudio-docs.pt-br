---
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a3f3c2dca16cd2c28c9d1727e4ac145c91c482
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720690"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Essa interface fornece as funções que permitem obter e definir uma propriedade.

## <a name="syntax"></a>Syntax

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa o [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Essa interface é uma especialização que dá suporte ao conceito de propriedades em uma classe.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obter essa interface da interface [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) se o método [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retornar `FIELD_KIND_PROP` .

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Além dos métodos nas interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Obtém o método que obtém a propriedade.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Obtém o método que define a propriedade.|

## <a name="remarks"></a>Comentários
 Uma propriedade é um conceito de código gerenciado e representa um método que é tratado como uma variável. As propriedades não existem no C++ não gerenciado.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

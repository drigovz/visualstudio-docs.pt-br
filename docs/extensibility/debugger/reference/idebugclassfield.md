---
title: IDebugClassField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b0e4cd7c851e65edf299f45ec97273804c25d8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734293"
---
# <a name="idebugclassfield"></a>IDebugClassField
Esta interface representa uma classe como um tipo.

## <a name="syntax"></a>Sintaxe

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um provedor de símbolos implementa essa interface no mesmo objeto que implementa a interface [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Esta interface é uma especialização que representa um tipo de classe.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma série de interfaces têm métodos que podem retornar esta interface, incluindo [IDebugSymbolProvider,](../../../extensibility/debugger/reference/idebugsymbolprovider.md) [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)e [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Além disso, você pode usar [o QueryInterface](/cpp/atl/queryinterface) para obter esta interface a partir `FIELD_TYPE_CLASS`da interface [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) se o método [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retornar o sinalizador .

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos nas interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) esta interface implementa o seguinte:

|Método|Descrição|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Cria um enumerador para as classes base desta classe.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Determina se uma interface específica é definida na classe.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Cria um enumerador para as classes aninhadas desta classe.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Tem a classe que encerra essa aula.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Cria um enumerador para as interfaces implementadas por esta classe.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Cria um enumerador para os construtores desta classe.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Obtém o nome do indexador padrão.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Cria um enumerador para os enumeradores aninhados desta classe.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

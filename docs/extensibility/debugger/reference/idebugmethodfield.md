---
title: IDebugMethodField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061035933e57ea4ca8e7857f68ac3d6311bae32c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727067"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Esta interface descreve um método.

## <a name="syntax"></a>Sintaxe

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um provedor de símbolos implementa essa interface no mesmo objeto que implementa a interface [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Esta interface é uma especialização que apresenta um método.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [queryInterface](/cpp/atl/queryinterface) para obter esta interface a partir da `FIELD_TYPE_METHOD`interface [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) se [getKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retornar . Além disso, os métodos, [GetPropertyGetter,](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)e [EnumConstructors,](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)retornam a `IDebugMethodField` interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos nas interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Cria um enumerador para os parâmetros do método.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Obtém o ponteiro "este" do objeto que contém o método.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Cria um enumerador para todas as variáveis locais do método.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Cria um enumerador para variáveis locais selecionadas do método.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Determina se um atributo personalizado específico foi definido.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Cria um enumerador para variáveis locais estáticas do método.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Fica com o recipiente global do método.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Cria um enumerador para o tipo de argumento necessário para chamar o método.|

## <a name="remarks"></a>Comentários
 Um método pode conter parâmetros, bem como variáveis locais.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

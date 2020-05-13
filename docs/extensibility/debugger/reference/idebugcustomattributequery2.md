---
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe3969002c64ab361de76012c432e2bb5c61b5c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732480"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Determina a existência de um atributo personalizado para este campo e, se ele existir, retorna as informações de atributos.

## <a name="syntax"></a>Sintaxe

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um provedor de símbolos implementa essa interface no mesmo objeto que implementa o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) para suportar atributos personalizados.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [queryInterface](/cpp/atl/queryinterface) para obter esta interface a partir da interface [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir mostra os métodos da interface **IDebugCustomAttributeQuery.**

|Método|Descrição|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Determina se existe um atributo personalizado pelo nome.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Obtém as informações de atributo para o atributo personalizado dado.|

 Além dos métodos **IDebugCustomAttributeQuery,** `IDebugCustomAttributeQuery2` implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Obtém um enumerador para todos os atributos personalizados anexados a este campo.|

## <a name="remarks"></a>Comentários
 O método [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) pode retornar um enumerador para todos os atributos personalizados definidos para este campo.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

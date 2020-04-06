---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72296517a64c6dcfcb8e347fb00588504aa75a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733208"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Esta interface representa um símbolo ou tipo que é um recipiente para outros símbolos ou tipos.

## <a name="syntax"></a>Sintaxe

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um provedor de símbolos implementa essa interface no mesmo objeto que implementa a interface [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Esta interface também é a classe base para todas as interfaces que representam contêineres.

## <a name="notes-for-callers"></a>Observações para chamadores
 Muitos métodos em muitas interfaces retornam essa interface. Por se trata de uma classe base para todos os contêineres, interfaces mais especializadas podem ser obtidas a partir desta interface usando [o QueryInterface](/cpp/atl/queryinterface). Essas interfaces incluem [IDebugArrayField,](../../../extensibility/debugger/reference/idebugarrayfield.md) [IDebugClassField,](../../../extensibility/debugger/reference/idebugclassfield.md) [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos na interface [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) esta interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Cria um enumerador para os campos do recipiente.|

## <a name="remarks"></a>Comentários
 Matrizes (recipientes para variáveis), classes (recipientes para métodos e variáveis) e métodos (recipientes para parâmetros e variáveis locais) são todos exemplos de recipientes.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2e7ed9e573236f0bdeff9c9a8433af322a5a5f79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928491"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Essa interface representa um símbolo ou tipo que é um contêiner para outros símbolos ou tipos.

## <a name="syntax"></a>Sintaxe

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa a interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Essa interface também é a classe base para todas as interfaces que representam contêineres.

## <a name="notes-for-callers"></a>Observações para chamadores
 Muitos métodos em várias interfaces retornam essa interface. Como essa é uma classe base para todos os contêineres, interfaces mais especializadas podem ser obtidas nessa interface usando [QueryInterface](/cpp/atl/queryinterface). Essas interfaces incluem [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Além dos métodos na interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , essa interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Cria um enumerador para os campos do contêiner.|

## <a name="remarks"></a>Comentários
 Matrizes (contêineres para variáveis), classes (contêineres para métodos e variáveis) e métodos (contêineres para parâmetros e variáveis locais) são exemplos de contêineres.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

---
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e069a822cc2394769d256c93a1decf01b451b643
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944850"
---
# <a name="idebugaddress"></a>IDebugAddress
Essa interface representa o endereço de um item. Ele é retornado pelo manipulador de símbolo.

## <a name="syntax"></a>Sintaxe

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um provedor de símbolo implementa essa interface para representar um endereço de um objeto.

## <a name="notes-for-callers"></a>Observações para chamadores
 Muitos métodos em várias interfaces retornam essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Essa interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Recupera uma estrutura de [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) descrevendo um objeto e sua localização.|

## <a name="remarks"></a>Comentários
 O provedor de símbolos retorna essa interface para representar um objeto e sua localização dentro de um escopo específico (por exemplo, função, método ou classe). Essa interface é retornada e passada para vários métodos do provedor de símbolos e do avaliador de expressão. Normalmente, o provedor de símbolos é a única entidade que precisa interpretar o conteúdo dessa interface.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

---
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca7113a1b108713b5dd7cf0f17511cec39a1b8b6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695486"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Essa interface permite que um chamador determinar se um fornecedor de porta pode preservar as portas (gravá-los em disco) entre as invocações do depurador e, em seguida, obter uma lista dessas portas preservado.

## <a name="syntax"></a>Sintaxe

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um fornecedor de porta personalizada implementa essa interface para dar suporte a persistir ou salvar informações de porta para o disco. Esta interface deve ser implementada no mesmo objeto como o [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chame [QueryInterface](/cpp/atl/queryinterface) sobre o `IDebugPortSupplier2` interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos herdados do [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface, essa interface dá suporte para o seguinte:

|Método|Descrição|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Retorna se o fornecedor de porta pode persistir portas (gravando-os em disco) entre as invocações do depurador.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Retorna um objeto que pode ser usado para enumerar todas as portas que foram gravados no disco por esse fornecedor de porta.|

## <a name="remarks"></a>Comentários
 Se um fornecedor de porta pode persistir as portas entre invocações, ele deve implementar essa interface. As portas devem ser carregadas quando o fornecedor de porta é instanciado e gravado em disco quando o fornecedor de porta é destruído.

 Normalmente, um mecanismo de depuração não interage com um fornecedor de porta e não terá nenhum uso para essa interface.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
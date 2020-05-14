---
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724440"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Essa interface permite que um chamador determine se um fornecedor de portas pode preservar portas (escrevendo-as em disco) entre invocações do depurador e, em seguida, obter uma lista dessas portas preservadas.

## <a name="syntax"></a>Sintaxe

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um fornecedor de porta personalizado implementa essa interface para suportar a persistência ou salvar informações da porta em disco. Esta interface deve ser implementada no mesmo objeto que a interface [IDebugPortSupplier2.](../../../extensibility/debugger/reference/idebugportsupplier2.md)

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para a `IDebugPortSupplier2` [QueryInterface](/cpp/atl/queryinterface) na interface para obter esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 Além dos métodos herdados da interface [IDebugPortSupplier2,](../../../extensibility/debugger/reference/idebugportsupplier2.md) esta interface suporta o seguinte:

|Método|Descrição|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Retorna se o fornecedor de portas pode persistir portas (escrevendo-as em disco) entre invocações do depurador.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Retorna um objeto que pode ser usado para enumerar todas as portas que foram escritas em disco por este fornecedor de portas.|

## <a name="remarks"></a>Comentários
 Se um fornecedor de portas pode persistir portas através de invocações, ele deve implementar esta interface. As portas devem ser carregadas quando o fornecedor da porta estiver instanciado e gravado em disco quando o fornecedor da porta for destruído.

 Um mecanismo de depuração normalmente não interage com um fornecedor de porta e não terá uso para esta interface.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)

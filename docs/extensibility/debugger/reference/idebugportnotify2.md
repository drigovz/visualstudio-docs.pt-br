---
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1b1934a73e096200eba1370320cc0b55eb46ac5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308897"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Essa interface registra ou cancela o registro de um programa que pode ser depurado com a porta na que qual está sendo executado.

## <a name="syntax"></a>Sintaxe

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um fornecedor de porta personalizada implementa essa interface para dar suporte à adição e remoção de programas da porta. Ele geralmente é implementado no mesmo objeto que implementa o [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para [QueryInterface](/cpp/atl/queryinterface) sobre o `IDebugPort2` interface retorna essa interface. Além disso, uma chamada para [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) retorna essa interface. Um mecanismo de depuração pode ver essa interface como um parâmetro para [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugPortNotify2`.

|Método|Descrição|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra um programa que pode ser depurado com a porta na que qual está sendo executado.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Cancela o registro de um programa que pode ser depurado da porta do que qual está sendo executado.|

## <a name="remarks"></a>Comentários
 A menos que uma porta de depuração tem uma maneira de saber quando os programas são carregados ou descarregados, um fornecedor de porta personalizado deve implementar essa interface. Todos os programas que são carregados para a depuração por meio de uma porta específica são controlados usando esta interface.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
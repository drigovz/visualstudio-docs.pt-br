---
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d3d1161d488ed4a9e12b7af6b70bf336c9f286
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724925"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Esta interface registra ou desregistra um programa que pode ser depurado com a porta em que está sendo executado.

## <a name="syntax"></a>Sintaxe

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um fornecedor de porta personalizado implementa essa interface para suportar a adição e a remoção de programas da porta. É normalmente implementado no mesmo objeto que implementa a interface [IDebugPort2.](../../../extensibility/debugger/reference/idebugport2.md)

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para [QueryInterface](/cpp/atl/queryinterface) na `IDebugPort2` interface retorna esta interface. Além disso, uma chamada para [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) retorna esta interface. Um mecanismo de depuração pode ver esta interface como um parâmetro para [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugPortNotify2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra um programa que pode ser depurado com a porta em que está sendo executado.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Descadastramento de um programa que pode ser depurado da porta em que está sendo executado.|

## <a name="remarks"></a>Comentários
 A menos que uma porta de depuração tenha uma maneira de saber quando os programas são carregados ou descarregados, um fornecedor de porta personalizado deve implementar essa interface. Todos os programas carregados para depuração através de uma determinada porta são rastreados usando esta interface.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

---
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b32d2469c42931fa3dead4c5078e7d5b44b5d60
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334932"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Essa interface enumera os processos em execução em uma porta de depuração.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um fornecedor de porta personalizada implementa essa interface para fornecer uma lista de processos em execução em uma porta.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chamadas do Visual Studio [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IEnumDebugProcesses2`.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Recupera um número especificado de processos em uma sequência de enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Ignora um número especificado de processos em uma sequência de enumeração.|
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Obtém o número de processos em um enumerador.|

## <a name="remarks"></a>Comentários
 O Visual Studio usa essa interface para preencher a **processos** janela.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
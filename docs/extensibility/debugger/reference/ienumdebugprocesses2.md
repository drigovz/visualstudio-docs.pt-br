---
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b9fe0e96ade081e8da11b5e1c06c5b45279b10b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715752"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Esta interface enumera os processos em execução em uma porta de depuração.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um fornecedor de porta personalizado implementa essa interface para fornecer uma lista de processos em execução em uma porta.

## <a name="notes-for-callers"></a>Observações para chamadores
 O Visual Studio chama [a EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IEnumDebugProcesses2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Recupera um número especificado de processos em uma seqüência de enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Salta um número especificado de processos em uma seqüência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Reinicia uma seqüência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Obtém o número de processos em um enumerador.|

## <a name="remarks"></a>Comentários
 O Visual Studio usa essa interface para preencher a janela **Processos.**

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)

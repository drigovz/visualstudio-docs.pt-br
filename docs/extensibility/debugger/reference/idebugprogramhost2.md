---
title: IDebugProgramHost2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64db456e0c438f8665f122c3cd1b079c2ad1cea1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722216"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Esta interface fornece informações host (processo) sobre um programa.

## <a name="syntax"></a>Sintaxe

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração implementa essa interface no mesmo objeto da interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) para fornecer informações sobre o processo de hospedagem. Esta é uma interface opcional.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para o `IDebugProgram2` [QueryInterface](/cpp/atl/queryinterface) em uma interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugProgramHost2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Obtém o título, nome amigável ou nome do arquivo do processo de hospedagem deste programa.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Obtém o identificador de processo do processo de hospedagem deste programa.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Recebe o nome da máquina o processo de hospedagem deste programa está sendo executado.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

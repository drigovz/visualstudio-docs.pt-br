---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715576"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Essa interface enumera os programas em execução na sessão de depuração atual.

## <a name="syntax"></a>Syntax

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface para fornecer uma lista de programas que estão sendo depurados pelo DE.

## <a name="notes-for-callers"></a>Observações para chamadores
 O Visual Studio chama [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) para obter essa interface. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) não é usado pelo Visual Studio.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A tabela a seguir mostra os métodos de `IEnumDebugPrograms2` .

|Método|Descrição|
|------------|-----------------|
|[Próximo](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera um número especificado de programas em uma sequência de enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignora um número especificado de programas em uma sequência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtém o número de programas em um enumerador.|

## <a name="remarks"></a>Comentários
 O Visual Studio usa essa interface para:

- Preencha a janela **módulos** (chamando [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) e, em seguida, chamando [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) em cada programa).

- Popule a lista **Attach to Process** (chamando `IDebugProcess2::EnumPrograms` e, em seguida, chamando [QueryInterface](/cpp/atl/queryinterface) em cada interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) para obter uma interface [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) ).

- Gere uma lista de DEs que possa depurar cada programa no processo (usando [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Aplique atualizações do ENC (Edit and Continue) a cada programa (chamando IDebugProcess2:: EnumPrograms e, em seguida, chamando [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

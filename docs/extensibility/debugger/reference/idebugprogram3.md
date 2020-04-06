---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9da63d54f64a4ef7592fdbc4d36e2b31220f82df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722648"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Esta interface representa um programa que está sendo executado em um processo e estende [o Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) fornecendo informações de segmento.

## <a name="syntax"></a>Sintaxe

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) e um fornecedor de porta personalizado implementam essa interface para representar um programa em um processo. O SDM (Session Debug Manager, gerenciador de depuração de sessão) também implementa essa interface para fornecer informações ao [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Observações para chamadores
 O evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) retorna esta interface para um novo programa. Esta interface também é usada como parâmetro para muitos métodos em múltiplas interfaces.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugProgram3`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Executa o programa. O segmento é retornado para dar ao depurador informações sobre qual segmento o usuário está visualizando ao executar.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Comentários
 Um programa é um contêiner de thread em execução em uma arquitetura de tempo de execução particular, enquanto um processo é composto por um ou mais programas.

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Avançar](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

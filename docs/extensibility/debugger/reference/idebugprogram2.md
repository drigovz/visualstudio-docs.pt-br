---
title: IDebugProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 150746197be4945b012717bef08e18ea57168177
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722726"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Esta interface representa um programa que está sendo executado em um processo.

## <a name="syntax"></a>Sintaxe

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) e um fornecedor de porta personalizado implementam essa interface para representar um programa em um processo. O SDM (Session Debug Manager, gerenciador de depuração de sessão) também implementa essa interface para fornecer informações ao [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Observações para chamadores
 O evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) retorna esta interface para um novo programa. Esta interface também é usada como parâmetro para muitos métodos em múltiplas interfaces.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugProgram2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Enumera os segmentos que estão sendo executados neste programa.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Fica o nome do programa.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Fica o processo em que este programa está sendo executado.|
|[Encerrar](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Termina este programa.|
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Anexa-se a este programa.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Determina se um motor de depuração (DE) pode se desprender do programa.|
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Destaca o depurador deste programa.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Obtém um identificador globalmente único para este programa.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Obtém propriedades do programa.|
|[Executar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua executando este programa de um estado parado. Qualquer estado de execução anterior é liberado.|
|[Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua executando este programa de um estado parado. Qualquer estado de execução anterior está preservado.|
|[Etapa](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Realiza um passo.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Solicita que este programa interrompa a execução na próxima vez que um de seus threads for executado código.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Obtém o nome e o identificador do mecanismo de depuração (DE) executando este programa.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Enumera os contextos de código para uma determinada posição em um arquivo de origem.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Obtém os bytes de memória para este programa.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Obtém o fluxo de desmontagem para este programa ou parte deste programa.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Enumera os módulos que este programa carregou e está executando.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Obtém a atualização Editar e Continuar (ENC) para este programa.<br /><br /> Um mecanismo de depuração personalizado não implementa este método (ele deve sempre retornar `E_NOTIMPL`).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Enumera os caminhos de código deste programa.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Escreve um despejo em um arquivo.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Comentários
 Um programa é um contêiner de thread em execução em uma arquitetura de tempo de execução particular, enquanto um processo é composto por um ou mais programas.

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Avançar](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

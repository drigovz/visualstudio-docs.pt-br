---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b423ee2cb95ad55296c452cfdc4b891ee4cd26a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723535"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Esta interface representa um processo em execução e seus programas. Essa interface existe como uma substituição a vários métodos na interface [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) Fornece controle sobre todos os programas no processo.

> [!NOTE]
> [Os](../../../extensibility/debugger/reference/idebugprogram2-continue.md)métodos [Continue, Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)e [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) sejam preteridos e não devem mais ser usados. Use os métodos `IDebugProcess3` correspondentes na interface.

## <a name="syntax"></a>Sintaxe

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface é implementada por um fornecedor de porto personalizado para gerenciar programas em grupo. Quando os programas são gerenciados como um grupo, você pode controlar sua execução e estabelecer uma linguagem para um avaliador de expressão. Esta interface deve ser implementada pelo fornecedor portuário.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é chamada principalmente pelo Session Debug Manager (SDM) para interagir com um grupo de programas identificados nesse processo.

 Chamada [QueryInterface](/cpp/atl/queryinterface) em uma interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) para obter esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos herdados do [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) `IDebugProcess3` implementa os seguintes métodos.

|Método|Descrição|
|------------|-----------------|
|[Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continua a execução ou passo através de um processo.|
|[Executar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Começa a execução de um processo.|
|[Etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Passos adiante uma instrução ou declaração no processo.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Fica a razão pela qual o processo foi lançado para depuração.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Define o idioma de hospedagem para que o mecanismo de depuração possa carregar o avaliador de expressão apropriado.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera o idioma atualmente definido para este processo.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Desabilita Editar e Continuar (ENC) para este processo.<br /><br /> Um fornecedor de porto personalizado não implementa este método (ele deve sempre retornar `E_NOTIMPL`).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Obter o estado ENC para este processo.<br /><br /> Um fornecedor de porto personalizado não implementa este método (ele deve sempre retornar `E_NOTIMPL`).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera uma matriz de identificadores exclusivos para motores de depuração disponíveis.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
